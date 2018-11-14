```rust
use crossbeam_channel as channel;
use expect_macro::expect;
use rayon::prelude::*;
use reqwest::{Client, Proxy};
use serde_derive::Deserialize;
use std::thread;

#[derive(Debug, Deserialize)]
struct Item {
    id: u64,
    score: u64,
    by: String,
    title: String,
}

fn get_news() {
    std::panic::set_hook(Box::new(|panic_info| {
        eprintln!("{}", panic_info.to_string());
    }));

    let client = Client::builder()
        .proxy(Proxy::all("http://sg-sd27b-1.isid.co.jp:8080").unwrap())
        .build()
        .expect("");

    let mut res = client
        .get("https://hacker-news.firebaseio.com/v0/topstories.json")
        .send()
        .unwrap();

    let items: Vec<u64> = expect!(res.json());
    let len = 30;
    // println!("{:?}", &items[0..len]);
    let items_clone = items.clone();
    let (tx, rx): (channel::Sender<Item>, channel::Receiver<Item>) = channel::unbounded();
    let receiver_thread = thread::spawn(move || {
        let mut items = Vec::new();
        for item in rx {
            items.push(item);
        }
        items.sort_by(|a, b| {
            items_clone
                .iter()
                .position(|&x| x == a.id)
                .cmp(&items_clone.iter().position(|&x| x == b.id))
        });
        for item in items {
            println!("{}", item.title);
        }
    });

    let pool = rayon::ThreadPoolBuilder::new()
        .num_threads(4)
        .build()
        .unwrap();

    pool.install(|| {
        items[0..len]
            .into_par_iter()
            .for_each_with(tx, |tx_ref, entry| {
                let mut res = client
                    .get(&format!(
                        "https://hacker-news.firebaseio.com/v0/item/{}.json",
                        entry
                    ))
                    .send()
                    .unwrap();
                let item: Item = expect!(res.json());
                tx_ref.send(item).unwrap();
            });
    });
    receiver_thread.join().unwrap();
}

fn main() {
    get_news();
}
```
