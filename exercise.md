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
```js
let arr = ["helLo wORld", "hOW aRe yOu", "WHY aRE u"]; // dummy array of strings

// anonymous
let toTitle = function(arr) {
    console.log("Output using anonymous: ");
    for(let str of arr) {
        let upper = true;
        let newStr = "";
        
        for(let ch of str) {
            if(ch == " ") {
                upper = true;
                newStr += ch;
                continue;
            }
            newStr += upper ? ch.toUpperCase() : ch.toLowerCase();
            upper = false;
        }
        console.log(newStr);
    }
}

toTitle(arr);

// IIFE
(function(arr) {
    console.log("Output using IIFE: ");
    for(let str of arr) {
        let upper = true;
        let newStr = "";
        
        for(let ch of str) {
            if(ch == " ") {
                upper = true;
                newStr += ch;
                continue;
            }
            newStr += upper ? ch.toUpperCase() : ch.toLowerCase();
            upper = false;
        }
        console.log(newStr);
    }
})(arr);
```
> Output using anonymous:   
  Hello World  
  How Are You  
  Why Are U    
  Output using IIFE:   
  Hello World  
  How Are You  
  Why Are U  
3. sum of nos in array:
```js
let arr = [10, 1486, 2885, 17456, 155]; // dummy array of nos
// anonymous
let sum = function(arr) {
    console.log("Output using anonymous: ");
    let result = 0;
    for(let num of arr) {
        result += num;
    }
    console.log(`Sum = ${result}`);
}

sum(arr);

// IIFE
(function(arr) {
    console.log("Output using IIFE: ");
    let result = 0;
    for(let num of arr) {
        result += num;
    }
    console.log(`Sum = ${result}`);
})(arr);
```
> Output using anonymous:   
Sum = 21992  
Output using IIFE:   
Sum = 21992  
4. return prime nos in array:
```js
let arr = [4, 2, 7, 23, 37, 18, 13, 33, 81, 101]; // dummy array of nums
// anonymous
let findPrimes = function(arr) {
    let primes = [];
    for(let num of arr) {
        if(num % 2 === 0) {
            continue;
        }
        let isPrime = true;
        for(let i = 3; i < num ** 0.5 + 1; i += 2) {
            if(num % i === 0) {
                isPrime = false;
                break;
            }
        }
        if(isPrime) {
            primes.push(num);
        }
    }
    return primes;
}

console.log(`primes using anonymous: ${findPrimes(arr)}`);

// IIFE
(function(arr) {
    let primes = [];
    for(let num of arr) {
        if(num % 2 === 0) {
            continue;
        }
        let isPrime = true;
        for(let i = 3; i < num ** 0.5 + 1; i += 2) {
            if(num % i === 0) {
                isPrime = false;
                break;
            }
        }
        if(isPrime) {
            primes.push(num);
        }
    }
    console.log(`primes using IIFE: ${primes}`);
})(arr);
```
> primes using anonymous: 7,23,37,13,101  
  primes using IIFE: 7,23,37,13,101
5. Palindromes in array:
```js
let arr = ["helloolleh", "mam", "movie", "1881", "131", "world"];
// anonymous
let findPalindromes = function(arr) {
    let palindromes = [];
    for(let str of arr) {
        let len = str.length;
        let isPalindrome = true;
        for(let i = 0; i < Math.floor(len / 2); i++) {
            if(str[i] !== str[len - 1 - i]) {
                isPalindrome = false;
                break;
            }
        }
        if(isPalindrome) {
            palindromes.push(str);
        }
    }
    return palindromes;
}

console.log(`palindromes using anonymous: ${findPalindromes(arr)}`);

// IIFE
(function(arr) {
    let palindromes = [];
    for(let str of arr) {
        let len = str.length;
        let isPalindrome = true;
        for(let i = 0; i < Math.floor(len / 2); i++) {
            if(str[i] !== str[len - 1 - i]) {
                isPalindrome = false;
                break;
            }
        }
        if(isPalindrome) {
            palindromes.push(str);
        }
    }
    console.log(`palindromes using IIFE: ${palindromes}`);
})(arr);
```
> palindromes using anonymous: helloolleh,mam,1881,131  
  palindromes using IIFE: helloolleh,mam,1881,131
6. Median of 2 sorted arrays of same size
```js
let arr1 = [2, 5, 7, 19, 20, 17];
let arr2 = [4, 6, 7, 12, 18, 21];
// anonymous
let findMedian = function(arr1, arr2) {
    let len = arr1.length;
    let newSorted = [];
    let counter = 0;
    let i = 0;
    let j = 0;
    while(true) {
        if(arr1[i] < arr2[j]) {
            newSorted.push(arr1[i]);
            i++;
            counter++;
        } else if(arr2[j] < arr1[i]) {
            newSorted.push(arr2[j]);
            j++;
            counter++;
        } else {
            newSorted.push(arr1[i]);
            newSorted.push(arr2[j]);
            i++;
            j++;
            counter += 2;
        }
        if(counter >= len + 1) {
            break;
        }
    }
    return (newSorted[len - 1] + newSorted[len]) / 2;
}

console.log(`Median anonymous: ${findMedian(arr1, arr2)}`);

// IIFE
(function(arr1, arr2) {
    let len = arr1.length;
    let newSorted = [];
    let counter = 0;
    let i = 0;
    let j = 0;
    while(true) {
        if(arr1[i] < arr2[j]) {
            newSorted.push(arr1[i]);
            i++;
            counter++;
        } else if(arr2[j] < arr1[i]) {
            newSorted.push(arr2[j]);
            j++;
            counter++;
        } else {
            newSorted.push(arr1[i]);
            newSorted.push(arr2[j]);
            i++;
            j++;
            counter += 2;
        }
        if(counter >= len + 1) {
            break;
        }
    }
    console.log(`Median IIFE: ${(newSorted[len-1] + newSorted[len]) / 2}`);
})(arr1, arr2);
```
> Median anonymous: 9.5  
  Median IIFE: 9.5
7. Remove duplicates from array:
```js
let arr = [2, 5, "hello", 5, "hello", 2];
// anonymous
let removeDuplicates = function(arr) {
    let newArr = [];
    for(let element of arr) {
        if(!newArr.includes(element)) {
            newArr.push(element);
        }
    }
    return newArr;
};

console.log(`anonymous : ${removeDuplicates(arr)}`);

(function(arr) {
    let newArr = [];
    for(let element of arr) {
        if(!newArr.includes(element)) {
            newArr.push(element);
        }
    }
    console.log(`IIFE: ${newArr}`);
})(arr);
```
> anonymous : 2,5,hello  
  IIFE: 2,5,hello
8. Rotate array by k times:
```js
let arr = [1, 2, 3, "hello", "pip", 5, 7];
// anonymous
let rotate = function(arr, k) {
    if(arr.length > 1) {
        for(let i = 0; i < k; i++) {
            let first = arr.shift();
            arr.push(first);
        }
    }
    return arr;
}

console.log(`anonymous: ${rotate(arr, 2)}`);

// IIFE
arr = [1, 2, 3, "hello", "pip", 5, 7];

(function(arr, k) {
    if(arr.length > 1) {
        for(let i = 0; i < k; i++) {
            let first = arr.shift();
            arr.push(first);
        }
    }
    console.log(`IIFE: ${arr}`);
})(arr, 2);
```
> anonymous: 3,hello,pip,5,7,1,2  
  IIFE: 3,hello,pip,5,7,1,2




