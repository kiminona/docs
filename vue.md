```
 Error in render: "TypeError: Cannot read property 'length' of undefined"
 ```
 
 * 原因はundefined-value対するloopかもしれない。
 ```js
 v-for = (item in undefined)
  ```
