# Memoization

Memoization is an optimization technique that improves the performance of functions by storing the results of previous computations for the same inputs.

**Here's the process:**

1. **Cache**: A cache is created to store previously calculated results based on their input.
2. **Check**: When the function is called, it first checks the cache for the result with the current input.
3. **Reuse**: If the result is found in the cache, it's returned immediately, avoiding redundant calculations.
4. **Compute & Store**: If the result isn't cached, the function performs the calculation, stores the result for the input in the cache, and then returns the result.

### Benefits:

1. Improves performance for repeatedly called functions with expensive computations.
2. Reduces redundant calculations and memory usage.

### Real-world use cases:

1. **Expensive Calculations**: Memoization is useful for functions involving complex calculations like Fibonacci sequence, factorial, or dynamic programming algorithms.
2. **Data Fetching**: When repeatedly fetching data from APIs or local storage, you can avoid redundant requests by caching the retrieved data with its input parameters.
3. **UI Components**: In React applications, memoizing expensive rendering logic for components with frequent re-renders can significantly improve performance.

### Simple Example:

```js
let sum = 0;

const calcFn = (num) => {
  for (let i = 0; i < num; i++) {
    sum += num;
  }
  return sum;
};

const memozie = (func) => {
  const cache = {};
  return function (...args) {
    let n = args[0];
    if (n in cache) {
      console.log("Inside Cache");
      return cache[n];
    }
    console.log("Calculating For the First Time");
    cache[n] = calcFn(n);
    return cache[n];
  };
};

console.time();
const effecient = memozie(calcFn);
console.log("Result: ", effecient(5));
console.timeEnd();

console.time();
console.log("Result2: ", effecient(5));
console.timeEnd();

/**
 * Log:
 *
 * Calculating For the First Time
 * Result:  25
 * default: 10.002ms
 * Inside Cache
 * Result2:  25
 * default: 0.861ms
 */
```

### Fibonnacci

```js
let count = 0;
function fibonacciMemoized(n, cache = {}) {
  if (n in cache) {
    count++;
    console.log("Cache count :", count);
    return cache[n];
  } else {
    if (n <= 1) {
      return n;
    } else {
      const result =
        fibonacciMemoized(n - 1, cache) + fibonacciMemoized(n - 2, cache);
      cache[n] = result;
      return result;
    }
  }
}

console.time();
const res = fibonacciMemoized(40); // Efficiently calculates fibonacci(40)
console.log("Result : ", res);
console.timeEnd();

/**
 * 
* Cache count : 1
Cache count : 2
Cache count : 3
Cache count : 4
Cache count : 5
Cache count : 6
Cache count : 7
Cache count : 8
Cache count : 9
Cache count : 10
Cache count : 11
Cache count : 12
Cache count : 13
Cache count : 14
Cache count : 15
Cache count : 16
Cache count : 17
Cache count : 18
Cache count : 19
Cache count : 20
Cache count : 21
Cache count : 22
Cache count : 23
Cache count : 24
Cache count : 25
Cache count : 26
Cache count : 27
Cache count : 28
Cache count : 29
Cache count : 30
Cache count : 31
Cache count : 32
Cache count : 33
Cache count : 34
Cache count : 35
Cache count : 36
Cache count : 37
Result :  102334155
default: 33.79ms
 */
```

### Leet Code: 2623. Memoize

Given a function fn, return a memoized version of that function.

A memoized function is a function that will never be called twice with the same inputs. Instead it will return a cached value.

You can assume there are 3 possible input functions: sum, fib, and factorial.

sum accepts two integers a and b and returns a + b.
fib accepts a single integer n and returns 1 if n <= 1 or fib(n - 1) + fib(n - 2) otherwise.
factorial accepts a single integer n and returns 1 if n <= 1 or factorial(n - 1) \* n otherwise.

```js
/**
 * @param {Function} fn
 * @return {Function}
 */
function memoize(fn) {
  const cache = {};

  return function (...args) {
    const key = JSON.stringify(args);
    if (key in cache) {
      return cache[key];
    }
    cache[key] = fn(...args);
    return cache[key];
  };
}

/**
 * let callCount = 0;
 * const memoizedFn = memoize(function (a, b) {
 *	 callCount += 1;
 *   return a + b;
 * })
 * memoizedFn(2, 3) // 5
 * memoizedFn(2, 3) // 5
 * console.log(callCount) // 1
 */
```
