### Q1- using anonymous and IIFE
1. print odd nos in an array
```js
let arr = [2, 19, 4, 13, 145, 12, 139, 157];
// anonymous
let printOdd = function(arr) {
  console.log("Output using anonymous: ")
  for(let num of arr) {
    if(num % 2 !== 0) {
      console.log(num);
    }
  }
};
printOdd(arr);

// IIFE
(function(arr) {
  console.log("Output using IIFE: ");
  for(let num of arr) {
    if(num % 2 !== 0) {
      console.log(num);
    }
  }
})(arr);
```
> Output using anonymous:   
  19  
  13  
  145  
  139  
  157  
  Output using IIFE:   
  19  
  13  
  145  
  139  
  157  
2. convert strings to title cap



