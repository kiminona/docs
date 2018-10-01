### to avoid "Merge branch 'master' of … ?"
```
git pull --rebase
```
https://github.com/choelea/tech-docs/blob/master/Dev-Ops/Git-Commands.md

https://github.com/qianzhangsheng/qianzhangsheng.github.io/issues/45


### git rebase
```bash
# Config git
git config --global sequence.editor git-interactive-rebase-tool
# Uninstall
git config --global --unset sequence.editor

# list
git log --oneline
# rebase
git rebase -i コミットid
```
https://qiita.com/tsuuuuu_san/items/f708a9f7ea8ab8eb6945
