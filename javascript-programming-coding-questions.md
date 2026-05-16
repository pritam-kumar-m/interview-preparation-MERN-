# 100 JavaScript Programming and Coding Questions with Answers

Prepared for interview coding practice for a full-stack developer around a 6-year experience level. Problems start with fundamentals, then move into practical utility functions, async JavaScript, polyfills, caching, queues, and production-style helpers.

**Question count:** 100

## Beginner

### 1. Reverse a string.

**Solution:**

```javascript
function reverseString(str) {
  return str.split('').reverse().join('');
}
```

**Explanation:** Split the string into characters, reverse the array, then join it back into a string.

### 2. Check whether a string is a palindrome.

**Solution:**

```javascript
function isPalindrome(str) {
  const s = str.toLowerCase().replace(/[^a-z0-9]/g, '');
  return s === s.split('').reverse().join('');
}
```

**Explanation:** Normalize the string first so spaces, punctuation, and casing do not affect the result.

### 3. Find the factorial of a number.

**Solution:**

```javascript
function factorial(n) {
  let result = 1;
  for (let i = 2; i <= n; i++) result *= i;
  return result;
}
```

**Explanation:** Multiply all integers from 2 to n; factorial of 0 and 1 remains 1.

### 4. Return the nth Fibonacci number.

**Solution:**

```javascript
function fibonacci(n) {
  if (n <= 1) return n;
  let a = 0, b = 1;
  for (let i = 2; i <= n; i++) [a, b] = [b, a + b];
  return b;
}
```

**Explanation:** Track only the previous two numbers to keep memory constant.

### 5. Calculate the sum of an array.

**Solution:**

```javascript
function sumArray(nums) {
  return nums.reduce((sum, n) => sum + n, 0);
}
```

**Explanation:** reduce accumulates the running total starting from 0.

### 6. Find the maximum number in an array.

**Solution:**

```javascript
function maxNumber(nums) {
  return Math.max(...nums);
}
```

**Explanation:** Spread passes all array values to Math.max; for huge arrays, use reduce to avoid argument limits.

### 7. Find the minimum number in an array.

**Solution:**

```javascript
function minNumber(nums) {
  return nums.reduce((min, n) => n < min ? n : min, nums[0]);
}
```

**Explanation:** Keep the smallest value seen while iterating through the array.

### 8. Count vowels in a string.

**Solution:**

```javascript
function countVowels(str) {
  const matches = str.match(/[aeiou]/gi);
  return matches ? matches.length : 0;
}
```

**Explanation:** A regular expression finds vowel matches; handle null when no vowel exists.

### 9. Remove duplicate values from an array.

**Solution:**

```javascript
function removeDuplicates(arr) {
  return [...new Set(arr)];
}
```

**Explanation:** Set stores unique values, and spreading converts it back to an array.

### 10. Return only even numbers from an array.

**Solution:**

```javascript
function getEvenNumbers(nums) {
  return nums.filter(n => n % 2 === 0);
}
```

**Explanation:** filter keeps only values that satisfy the condition.

### 11. Return only odd numbers from an array.

**Solution:**

```javascript
function getOddNumbers(nums) {
  return nums.filter(n => Math.abs(n % 2) === 1);
}
```

**Explanation:** Using Math.abs handles negative odd numbers correctly.

### 12. Capitalize the first character of a string.

**Solution:**

```javascript
function capitalize(str) {
  if (!str) return str;
  return str[0].toUpperCase() + str.slice(1);
}
```

**Explanation:** Handle empty strings first, then uppercase the first character.

### 13. Convert a sentence to title case.

**Solution:**

```javascript
function titleCase(sentence) {
  return sentence.split(' ').map(word =>
    word ? word[0].toUpperCase() + word.slice(1).toLowerCase() : word
  ).join(' ');
}
```

**Explanation:** Transform each word independently and join the result back.

### 14. Count words in a sentence.

**Solution:**

```javascript
function countWords(sentence) {
  const words = sentence.trim().split(/\s+/).filter(Boolean);
  return words.length;
}
```

**Explanation:** Trim and split on one or more whitespace characters to avoid counting extra spaces.

### 15. Find the longest word in a sentence.

**Solution:**

```javascript
function longestWord(sentence) {
  return sentence.split(/\s+/).reduce((longest, word) =>
    word.length > longest.length ? word : longest, ''
  );
}
```

**Explanation:** Compare each word length and keep the longest seen so far.

### 16. Find the second largest number in an array.

**Solution:**

```javascript
function secondLargest(nums) {
  const unique = [...new Set(nums)].sort((a, b) => b - a);
  return unique.length >= 2 ? unique[1] : null;
}
```

**Explanation:** Remove duplicates first, sort descending, and return the second item if it exists.

### 17. Flatten an array by one level.

**Solution:**

```javascript
function flattenOneLevel(arr) {
  return arr.flat();
}
```

**Explanation:** Array.prototype.flat without an argument flattens one nested level.

### 18. Merge two arrays and keep unique values.

**Solution:**

```javascript
function mergeUnique(a, b) {
  return [...new Set([...a, ...b])];
}
```

**Explanation:** Combine both arrays, then use Set to remove duplicates.

### 19. Check whether a number is prime.

**Solution:**

```javascript
function isPrime(n) {
  if (n < 2) return false;
  for (let i = 2; i * i <= n; i++) {
    if (n % i === 0) return false;
  }
  return true;
}
```

**Explanation:** Only test divisors up to the square root because larger factors pair with smaller ones.

### 20. Print FizzBuzz from 1 to n.

**Solution:**

```javascript
function fizzBuzz(n) {
  const result = [];
  for (let i = 1; i <= n; i++) {
    if (i % 15 === 0) result.push('FizzBuzz');
    else if (i % 3 === 0) result.push('Fizz');
    else if (i % 5 === 0) result.push('Buzz');
    else result.push(String(i));
  }
  return result;
}
```

**Explanation:** Check divisibility by 15 first so numbers divisible by both 3 and 5 are handled correctly.

### 21. Count character frequency in a string.

**Solution:**

```javascript
function charFrequency(str) {
  const freq = {};
  for (const ch of str) freq[ch] = (freq[ch] || 0) + 1;
  return freq;
}
```

**Explanation:** Use an object as a frequency map and increment each character count.

### 22. Check whether two strings are anagrams.

**Solution:**

```javascript
function areAnagrams(a, b) {
  const normalize = s => s.toLowerCase().replace(/[^a-z0-9]/g, '').split('').sort().join('');
  return normalize(a) === normalize(b);
}
```

**Explanation:** Normalize both strings and compare their sorted characters.

### 23. Sort numbers in ascending order.

**Solution:**

```javascript
function sortAscending(nums) {
  return [...nums].sort((a, b) => a - b);
}
```

**Explanation:** Use a numeric comparator because default sort compares values as strings.

### 24. Remove falsy values from an array.

**Solution:**

```javascript
function removeFalsy(arr) {
  return arr.filter(Boolean);
}
```

**Explanation:** Boolean converts each item to truthy/falsy and filter keeps truthy values.

### 25. Truncate a string to a maximum length.

**Solution:**

```javascript
function truncate(str, max) {
  if (str.length <= max) return str;
  return str.slice(0, Math.max(0, max - 3)) + '...';
}
```

**Explanation:** Return the original string if short enough; otherwise reserve space for ellipsis.

### 26. Split an array into chunks.

**Solution:**

```javascript
function chunkArray(arr, size) {
  const chunks = [];
  for (let i = 0; i < arr.length; i += size) chunks.push(arr.slice(i, i + size));
  return chunks;
}
```

**Explanation:** Move forward by chunk size and slice each group.

### 27. Find the intersection of two arrays.

**Solution:**

```javascript
function intersection(a, b) {
  const setB = new Set(b);
  return [...new Set(a)].filter(x => setB.has(x));
}
```

**Explanation:** Use a Set for fast membership checks and remove duplicates from the result.

### 28. Find values in the first array that are not in the second.

**Solution:**

```javascript
function difference(a, b) {
  const setB = new Set(b);
  return a.filter(x => !setB.has(x));
}
```

**Explanation:** Keep only values that do not appear in the second array.

### 29. Calculate the sum of digits in a number.

**Solution:**

```javascript
function sumDigits(num) {
  return Math.abs(num).toString().split('').reduce((sum, d) => sum + Number(d), 0);
}
```

**Explanation:** Convert the absolute number to digits and add each digit.

### 30. Convert Celsius to Fahrenheit.

**Solution:**

```javascript
function celsiusToFahrenheit(celsius) {
  return (celsius * 9 / 5) + 32;
}
```

**Explanation:** Use the standard conversion formula F = C * 9/5 + 32.

## Intermediate

### 31. Implement debounce.

**Solution:**

```javascript
function debounce(fn, delay) {
  let timer;
  return function (...args) {
    clearTimeout(timer);
    timer = setTimeout(() => fn.apply(this, args), delay);
  };
}
```

**Explanation:** Debounce waits until calls stop for the delay period before running the function.

### 32. Implement throttle.

**Solution:**

```javascript
function throttle(fn, delay) {
  let last = 0;
  return function (...args) {
    const now = Date.now();
    if (now - last >= delay) {
      last = now;
      fn.apply(this, args);
    }
  };
}
```

**Explanation:** Throttle allows execution at most once per delay window.

### 33. Deep clone a JSON-safe object.

**Solution:**

```javascript
function deepCloneJson(value) {
  return JSON.parse(JSON.stringify(value));
}
```

**Explanation:** This works for JSON-safe data but loses Date, undefined, functions, Map, Set, and circular references.

### 34. Flatten a deeply nested array.

**Solution:**

```javascript
function flattenDeep(arr) {
  return arr.reduce((out, item) =>
    out.concat(Array.isArray(item) ? flattenDeep(item) : item), []
  );
}
```

**Explanation:** Recursively flatten nested arrays and concatenate values into one result.

### 35. Group an array of objects by a key.

**Solution:**

```javascript
function groupBy(items, key) {
  return items.reduce((groups, item) => {
    const groupKey = item[key];
    (groups[groupKey] ||= []).push(item);
    return groups;
  }, {});
}
```

**Explanation:** Use reduce to create arrays under each grouping key.

### 36. Count occurrences of array values.

**Solution:**

```javascript
function countOccurrences(arr) {
  return arr.reduce((map, item) => {
    map[item] = (map[item] || 0) + 1;
    return map;
  }, {});
}
```

**Explanation:** Each item becomes a key whose count is incremented.

### 37. Implement memoization for a pure function.

**Solution:**

```javascript
function memoize(fn) {
  const cache = new Map();
  return (...args) => {
    const key = JSON.stringify(args);
    if (cache.has(key)) return cache.get(key);
    const value = fn(...args);
    cache.set(key, value);
    return value;
  };
}
```

**Explanation:** Cache function results by argument key to avoid repeated expensive calculations.

### 38. Implement a function that runs only once.

**Solution:**

```javascript
function once(fn) {
  let called = false;
  let result;
  return function (...args) {
    if (!called) {
      called = true;
      result = fn.apply(this, args);
    }
    return result;
  };
}
```

**Explanation:** Closure stores whether the function has already executed and returns the first result later.

### 39. Implement curried addition.

**Solution:**

```javascript
function add(a) {
  return function (b) {
    return a + b;
  };
}

add(2)(3); // 5
```

**Explanation:** The first call stores a in a closure, and the second call receives b.

### 40. Implement function composition.

**Solution:**

```javascript
function compose(...fns) {
  return value => fns.reduceRight((acc, fn) => fn(acc), value);
}
```

**Explanation:** compose runs functions from right to left, passing each result to the previous function.

### 41. Implement pipe.

**Solution:**

```javascript
function pipe(...fns) {
  return value => fns.reduce((acc, fn) => fn(acc), value);
}
```

**Explanation:** pipe runs functions left to right, which often reads like a data transformation flow.

### 42. Create a delay promise.

**Solution:**

```javascript
function delay(ms) {
  return new Promise(resolve => setTimeout(resolve, ms));
}
```

**Explanation:** Wrap setTimeout in a Promise so it can be awaited.

### 43. Retry an async function.

**Solution:**

```javascript
async function retry(fn, attempts = 3) {
  let lastError;
  for (let i = 0; i < attempts; i++) {
    try { return await fn(); }
    catch (err) { lastError = err; }
  }
  throw lastError;
}
```

**Explanation:** Try the async operation multiple times and throw the last error if all attempts fail.

### 44. Implement a simple Promise.all.

**Solution:**

```javascript
function promiseAll(promises) {
  return new Promise((resolve, reject) => {
    const results = [];
    let completed = 0;
    if (promises.length === 0) resolve([]);
    promises.forEach((p, i) => {
      Promise.resolve(p).then(value => {
        results[i] = value;
        completed++;
        if (completed === promises.length) resolve(results);
      }, reject);
    });
  });
}
```

**Explanation:** Resolve results in original order and reject immediately if any promise rejects.

### 45. Run async tasks sequentially.

**Solution:**

```javascript
async function runSequential(items, task) {
  const results = [];
  for (const item of items) results.push(await task(item));
  return results;
}
```

**Explanation:** Await inside a loop when each task must finish before the next starts.

### 46. Limit async concurrency.

**Solution:**

```javascript
async function mapLimit(items, limit, task) {
  const results = [];
  let index = 0;
  async function worker() {
    while (index < items.length) {
      const current = index++;
      results[current] = await task(items[current]);
    }
  }
  await Promise.all(Array.from({ length: limit }, worker));
  return results;
}
```

**Explanation:** Multiple workers share an index, ensuring no more than limit tasks run at once.

### 47. Parse a query string into an object.

**Solution:**

```javascript
function parseQuery(query) {
  return Object.fromEntries(new URLSearchParams(query.startsWith('?') ? query.slice(1) : query));
}
```

**Explanation:** URLSearchParams handles decoding and key-value parsing for standard query strings.

### 48. Build a query string from an object.

**Solution:**

```javascript
function buildQuery(params) {
  return new URLSearchParams(params).toString();
}
```

**Explanation:** URLSearchParams serializes object entries into a URL query string.

### 49. Convert a string to camelCase.

**Solution:**

```javascript
function toCamelCase(str) {
  return str.toLowerCase().replace(/[-_\s]+(.)?/g, (_, ch) => ch ? ch.toUpperCase() : '');
}
```

**Explanation:** Lowercase the input and uppercase characters after separators.

### 50. Convert a string to snake_case.

**Solution:**

```javascript
function toSnakeCase(str) {
  return str.replace(/([a-z])([A-Z])/g, '$1_$2').replace(/[\s-]+/g, '_').toLowerCase();
}
```

**Explanation:** Insert underscores between camelCase boundaries and replace spaces or hyphens.

### 51. Check deep equality for simple objects.

**Solution:**

```javascript
function deepEqual(a, b) {
  if (a === b) return true;
  if (typeof a !== 'object' || typeof b !== 'object' || !a || !b) return false;
  const keysA = Object.keys(a), keysB = Object.keys(b);
  if (keysA.length !== keysB.length) return false;
  return keysA.every(key => deepEqual(a[key], b[key]));
}
```

**Explanation:** Compare primitives directly, then recursively compare object keys and values.

### 52. Pick selected keys from an object.

**Solution:**

```javascript
function pick(obj, keys) {
  return keys.reduce((out, key) => {
    if (key in obj) out[key] = obj[key];
    return out;
  }, {});
}
```

**Explanation:** Build a new object containing only requested keys.

### 53. Omit selected keys from an object.

**Solution:**

```javascript
function omit(obj, keys) {
  const blocked = new Set(keys);
  return Object.fromEntries(Object.entries(obj).filter(([key]) => !blocked.has(key)));
}
```

**Explanation:** Filter out entries whose keys are in the omit list.

### 54. Get a nested value by path.

**Solution:**

```javascript
function getPath(obj, path, defaultValue) {
  const value = path.split('.').reduce((current, key) => current?.[key], obj);
  return value === undefined ? defaultValue : value;
}
```

**Explanation:** Walk each path segment safely with optional chaining.

### 55. Set a nested value by path.

**Solution:**

```javascript
function setPath(obj, path, value) {
  const keys = path.split('.');
  let current = obj;
  keys.slice(0, -1).forEach(key => current = current[key] ||= {});
  current[keys.at(-1)] = value;
  return obj;
}
```

**Explanation:** Create missing nested objects while walking the path, then assign the final value.

### 56. Create a simple EventEmitter.

**Solution:**

```javascript
class EventEmitter {
  constructor() { this.events = new Map(); }
  on(event, fn) { (this.events.get(event) || this.events.set(event, []).get(event)).push(fn); }
  emit(event, data) { (this.events.get(event) || []).forEach(fn => fn(data)); }
  off(event, fn) { this.events.set(event, (this.events.get(event) || []).filter(x => x !== fn)); }
}
```

**Explanation:** Store listeners by event name and call them when the event is emitted.

### 57. Implement a tiny LRU cache.

**Solution:**

```javascript
class LRUCache {
  constructor(limit) { this.limit = limit; this.map = new Map(); }
  get(key) {
    if (!this.map.has(key)) return undefined;
    const value = this.map.get(key);
    this.map.delete(key); this.map.set(key, value);
    return value;
  }
  set(key, value) {
    if (this.map.has(key)) this.map.delete(key);
    this.map.set(key, value);
    if (this.map.size > this.limit) this.map.delete(this.map.keys().next().value);
  }
}
```

**Explanation:** Map preserves insertion order, so refreshing a key moves it to the most recent position.

### 58. Convert a flat list to a tree.

**Solution:**

```javascript
function listToTree(items) {
  const byId = new Map(items.map(item => [item.id, { ...item, children: [] }]));
  const roots = [];
  for (const node of byId.values()) {
    if (node.parentId == null) roots.push(node);
    else byId.get(node.parentId)?.children.push(node);
  }
  return roots;
}
```

**Explanation:** Map nodes by ID first, then attach each node to its parent.

### 59. Flatten a tree to a list.

**Solution:**

```javascript
function treeToList(nodes) {
  const result = [];
  function visit(node) {
    const { children = [], ...rest } = node;
    result.push(rest);
    children.forEach(visit);
  }
  nodes.forEach(visit);
  return result;
}
```

**Explanation:** Depth-first traversal visits every node and stores a flat copy.

### 60. Validate a basic email string.

**Solution:**

```javascript
function isEmail(email) {
  return /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email);
}
```

**Explanation:** This is a practical basic check; production validation may need stricter business rules.

### 61. Return unique objects by key.

**Solution:**

```javascript
function uniqueBy(items, key) {
  const seen = new Set();
  return items.filter(item => {
    const value = item[key];
    if (seen.has(value)) return false;
    seen.add(value);
    return true;
  });
}
```

**Explanation:** Track seen key values and keep only the first object for each value.

### 62. Sort objects by a field.

**Solution:**

```javascript
function sortBy(items, key) {
  return [...items].sort((a, b) => a[key] > b[key] ? 1 : a[key] < b[key] ? -1 : 0);
}
```

**Explanation:** Copy before sorting to avoid mutating the original array.

### 63. Partition an array by a predicate.

**Solution:**

```javascript
function partition(arr, predicate) {
  return arr.reduce((groups, item) => {
    groups[predicate(item) ? 0 : 1].push(item);
    return groups;
  }, [[], []]);
}
```

**Explanation:** Store matching items in the first group and non-matching items in the second.

### 64. Move zeroes to the end.

**Solution:**

```javascript
function moveZeroes(nums) {
  const nonZero = nums.filter(n => n !== 0);
  return [...nonZero, ...Array(nums.length - nonZero.length).fill(0)];
}
```

**Explanation:** Keep non-zero values in order and append the required number of zeroes.

### 65. Rotate an array by k positions.

**Solution:**

```javascript
function rotateArray(arr, k) {
  const n = arr.length;
  k = ((k % n) + n) % n;
  return arr.slice(-k).concat(arr.slice(0, n - k));
}
```

**Explanation:** Normalize k and combine the last k items with the remaining prefix.

### 66. Implement binary search.

**Solution:**

```javascript
function binarySearch(nums, target) {
  let left = 0, right = nums.length - 1;
  while (left <= right) {
    const mid = Math.floor((left + right) / 2);
    if (nums[mid] === target) return mid;
    if (nums[mid] < target) left = mid + 1;
    else right = mid - 1;
  }
  return -1;
}
```

**Explanation:** Binary search halves the search range each step, so it requires sorted input.

### 67. Merge two sorted arrays.

**Solution:**

```javascript
function mergeSorted(a, b) {
  const result = [];
  let i = 0, j = 0;
  while (i < a.length && j < b.length) result.push(a[i] <= b[j] ? a[i++] : b[j++]);
  return result.concat(a.slice(i), b.slice(j));
}
```

**Explanation:** Use two pointers to merge in sorted order without resorting the full result.

### 68. Find two numbers that add to a target.

**Solution:**

```javascript
function twoSum(nums, target) {
  const seen = new Map();
  for (let i = 0; i < nums.length; i++) {
    const need = target - nums[i];
    if (seen.has(need)) return [seen.get(need), i];
    seen.set(nums[i], i);
  }
  return [];
}
```

**Explanation:** Store previous values in a map so each complement lookup is constant time.

### 69. Find maximum subarray sum.

**Solution:**

```javascript
function maxSubarraySum(nums) {
  let best = nums[0], current = nums[0];
  for (let i = 1; i < nums.length; i++) {
    current = Math.max(nums[i], current + nums[i]);
    best = Math.max(best, current);
  }
  return best;
}
```

**Explanation:** Kadane algorithm decides whether to extend the current subarray or start fresh.

## Advanced

### 70. Implement Promise.race.

**Solution:**

```javascript
function promiseRace(promises) {
  return new Promise((resolve, reject) => {
    promises.forEach(p => Promise.resolve(p).then(resolve, reject));
  });
}
```

**Explanation:** The first promise to settle decides the returned promise.

### 71. Implement Promise.allSettled.

**Solution:**

```javascript
function allSettled(promises) {
  return Promise.all(promises.map(p =>
    Promise.resolve(p)
      .then(value => ({ status: 'fulfilled', value }))
      .catch(reason => ({ status: 'rejected', reason }))
  ));
}
```

**Explanation:** Convert each promise into a fulfilled status object so Promise.all never rejects early.

### 72. Create an async pool with fixed concurrency.

**Solution:**

```javascript
async function asyncPool(limit, tasks) {
  const executing = new Set();
  const results = [];
  for (const task of tasks) {
    const promise = Promise.resolve().then(task);
    results.push(promise);
    executing.add(promise);
    promise.finally(() => executing.delete(promise));
    if (executing.size >= limit) await Promise.race(executing);
  }
  return Promise.all(results);
}
```

**Explanation:** Start tasks until the limit is reached, then wait for one to finish before starting another.

### 73. Create a cancellable timeout.

**Solution:**

```javascript
function cancellableTimeout(ms) {
  let timer;
  const promise = new Promise(resolve => { timer = setTimeout(resolve, ms); });
  return { promise, cancel: () => clearTimeout(timer) };
}
```

**Explanation:** Return both the promise and a cancel function that clears the timer.

### 74. Implement debounce with cancel.

**Solution:**

```javascript
function debounceWithCancel(fn, delay) {
  let timer;
  function debounced(...args) {
    clearTimeout(timer);
    timer = setTimeout(() => fn.apply(this, args), delay);
  }
  debounced.cancel = () => clearTimeout(timer);
  return debounced;
}
```

**Explanation:** Attach a cancel method so pending execution can be cleared manually.

### 75. Implement throttle with trailing call.

**Solution:**

```javascript
function throttleTrailing(fn, delay) {
  let last = 0, timer, lastArgs;
  return function (...args) {
    const remaining = delay - (Date.now() - last);
    lastArgs = args;
    if (remaining <= 0) {
      clearTimeout(timer); timer = null; last = Date.now(); fn.apply(this, args);
    } else if (!timer) {
      timer = setTimeout(() => { last = Date.now(); timer = null; fn.apply(this, lastArgs); }, remaining);
    }
  };
}
```

**Explanation:** Run immediately when allowed, otherwise schedule one trailing execution with the latest arguments.

### 76. Deep freeze an object.

**Solution:**

```javascript
function deepFreeze(obj) {
  Object.freeze(obj);
  Object.values(obj).forEach(value => {
    if (value && typeof value === 'object' && !Object.isFrozen(value)) deepFreeze(value);
  });
  return obj;
}
```

**Explanation:** Freeze the object and recursively freeze nested objects.

### 77. Flatten an object into dot-path keys.

**Solution:**

```javascript
function flattenObject(obj, prefix = '', out = {}) {
  for (const [key, value] of Object.entries(obj)) {
    const path = prefix ? prefix + '.' + key : key;
    if (value && typeof value === 'object' && !Array.isArray(value)) flattenObject(value, path, out);
    else out[path] = value;
  }
  return out;
}
```

**Explanation:** Recursively walk nested objects and store values under dot-separated paths.

### 78. Unflatten dot-path keys into an object.

**Solution:**

```javascript
function unflattenObject(flat) {
  const result = {};
  for (const [path, value] of Object.entries(flat)) {
    path.split('.').reduce((obj, key, i, keys) =>
      obj[key] ||= i === keys.length - 1 ? value : {}, result);
  }
  return result;
}
```

**Explanation:** Create nested objects for path segments and assign the final value.

### 79. Deep clone values including Date and RegExp.

**Solution:**

```javascript
function deepClone(value, seen = new WeakMap()) {
  if (value === null || typeof value !== 'object') return value;
  if (value instanceof Date) return new Date(value);
  if (value instanceof RegExp) return new RegExp(value);
  if (seen.has(value)) return seen.get(value);
  const clone = Array.isArray(value) ? [] : {};
  seen.set(value, clone);
  for (const key of Reflect.ownKeys(value)) clone[key] = deepClone(value[key], seen);
  return clone;
}
```

**Explanation:** Handle special objects and use WeakMap to avoid infinite recursion on circular references.

### 80. Implement custom bind.

**Solution:**

```javascript
function customBind(fn, context, ...boundArgs) {
  return function (...args) {
    return fn.apply(context, [...boundArgs, ...args]);
  };
}
```

**Explanation:** Store context and initial arguments in a closure, then apply them during invocation.

### 81. Implement custom map.

**Solution:**

```javascript
function customMap(arr, callback) {
  const result = [];
  for (let i = 0; i < arr.length; i++) result.push(callback(arr[i], i, arr));
  return result;
}
```

**Explanation:** Call the callback for each item and collect returned values.

### 82. Implement custom filter.

**Solution:**

```javascript
function customFilter(arr, callback) {
  const result = [];
  for (let i = 0; i < arr.length; i++) if (callback(arr[i], i, arr)) result.push(arr[i]);
  return result;
}
```

**Explanation:** Only push items when the callback returns a truthy value.

### 83. Implement custom reduce.

**Solution:**

```javascript
function customReduce(arr, callback, initialValue) {
  let i = 0;
  let acc = initialValue;
  if (acc === undefined) acc = arr[i++];
  for (; i < arr.length; i++) acc = callback(acc, arr[i], i, arr);
  return acc;
}
```

**Explanation:** Use the initial value if provided; otherwise start with the first array item.

### 84. Implement custom some.

**Solution:**

```javascript
function customSome(arr, callback) {
  for (let i = 0; i < arr.length; i++) {
    if (callback(arr[i], i, arr)) return true;
  }
  return false;
}
```

**Explanation:** Return true as soon as one item passes the callback test.

### 85. Implement custom every.

**Solution:**

```javascript
function customEvery(arr, callback) {
  for (let i = 0; i < arr.length; i++) {
    if (!callback(arr[i], i, arr)) return false;
  }
  return true;
}
```

**Explanation:** Return false as soon as one item fails the callback test.

### 86. Implement custom instanceof.

**Solution:**

```javascript
function customInstanceOf(obj, constructor) {
  let proto = Object.getPrototypeOf(obj);
  const target = constructor.prototype;
  while (proto) {
    if (proto === target) return true;
    proto = Object.getPrototypeOf(proto);
  }
  return false;
}
```

**Explanation:** Walk the prototype chain until the constructor prototype is found or the chain ends.

### 87. Create sleep that supports AbortSignal.

**Solution:**

```javascript
function sleep(ms, signal) {
  return new Promise((resolve, reject) => {
    if (signal?.aborted) return reject(new Error('Aborted'));
    const timer = setTimeout(resolve, ms);
    signal?.addEventListener('abort', () => {
      clearTimeout(timer);
      reject(new Error('Aborted'));
    }, { once: true });
  });
}
```

**Explanation:** Listen for abort and clear the timer if cancellation happens before completion.

### 88. Create a simple rate limiter.

**Solution:**

```javascript
function createRateLimiter(limit, windowMs) {
  const hits = new Map();
  return key => {
    const now = Date.now();
    const bucket = (hits.get(key) || []).filter(t => now - t < windowMs);
    if (bucket.length >= limit) return false;
    bucket.push(now); hits.set(key, bucket);
    return true;
  };
}
```

**Explanation:** Keep recent timestamps per key and allow requests only when count is below the limit.

### 89. Implement a sequential task queue.

**Solution:**

```javascript
class TaskQueue {
  constructor() { this.current = Promise.resolve(); }
  add(task) {
    const next = this.current.then(task, task);
    this.current = next.catch(() => {});
    return next;
  }
}
```

**Explanation:** Chain each task after the previous one so tasks run sequentially.

### 90. Implement a Pub/Sub utility.

**Solution:**

```javascript
function createPubSub() {
  const topics = new Map();
  return {
    subscribe(topic, fn) {
      (topics.get(topic) || topics.set(topic, new Set()).get(topic)).add(fn);
      return () => topics.get(topic)?.delete(fn);
    },
    publish(topic, value) {
      topics.get(topic)?.forEach(fn => fn(value));
    }
  };
}
```

**Explanation:** Store subscribers by topic and return an unsubscribe function for cleanup.

### 91. Create a minimal Observable.

**Solution:**

```javascript
function observable(subscribe) {
  return {
    subscribe(observer) {
      const safe = typeof observer === 'function' ? { next: observer } : observer;
      return subscribe(safe);
    }
  };
}
```

**Explanation:** An observable accepts a subscriber function and notifies observers through next/error/complete-style methods.

### 92. Retry with exponential backoff.

**Solution:**

```javascript
async function retryBackoff(fn, attempts = 3, baseMs = 100) {
  for (let i = 0; i < attempts; i++) {
    try { return await fn(); }
    catch (err) {
      if (i === attempts - 1) throw err;
      await new Promise(r => setTimeout(r, baseMs * 2 ** i));
    }
  }
}
```

**Explanation:** Wait longer after each failure so temporary downstream problems have time to recover.

### 93. Create a cache with TTL.

**Solution:**

```javascript
function createTTLCache() {
  const cache = new Map();
  return {
    set(key, value, ttlMs) { cache.set(key, { value, expires: Date.now() + ttlMs }); },
    get(key) {
      const item = cache.get(key);
      if (!item || item.expires < Date.now()) { cache.delete(key); return undefined; }
      return item.value;
    }
  };
}
```

**Explanation:** Store expiration time with each value and delete expired entries on read.

### 94. Memoize an async function.

**Solution:**

```javascript
function memoizeAsync(fn) {
  const cache = new Map();
  return (...args) => {
    const key = JSON.stringify(args);
    if (!cache.has(key)) cache.set(key, Promise.resolve(fn(...args)).catch(err => { cache.delete(key); throw err; }));
    return cache.get(key);
  };
}
```

**Explanation:** Cache the pending promise too, and remove failed promises so future calls can retry.

### 95. Topologically sort dependency nodes.

**Solution:**

```javascript
function topoSort(graph) {
  const visited = new Set(), visiting = new Set(), result = [];
  function visit(node) {
    if (visiting.has(node)) throw new Error('Cycle detected');
    if (visited.has(node)) return;
    visiting.add(node);
    (graph[node] || []).forEach(visit);
    visiting.delete(node); visited.add(node); result.push(node);
  }
  Object.keys(graph).forEach(visit);
  return result;
}
```

**Explanation:** Depth-first search adds dependencies before dependents and detects cycles with a visiting set.

### 96. Parse a simple CSV line.

**Solution:**

```javascript
function parseCsvLine(line) {
  const result = [];
  let value = '', quoted = false;
  for (let i = 0; i < line.length; i++) {
    const ch = line[i];
    if (ch === '"') quoted = !quoted;
    else if (ch === ',' && !quoted) { result.push(value); value = ''; }
    else value += ch;
  }
  result.push(value);
  return result;
}
```

**Explanation:** Track whether the parser is inside quotes so commas inside quoted values are not split.

### 97. Deep merge two objects.

**Solution:**

```javascript
function deepMerge(a, b) {
  const out = { ...a };
  for (const [key, value] of Object.entries(b)) {
    out[key] = value && typeof value === 'object' && !Array.isArray(value)
      ? deepMerge(out[key] || {}, value)
      : value;
  }
  return out;
}
```

**Explanation:** Merge nested plain objects recursively and let the second object override primitive values.

### 98. Stable stringify an object.

**Solution:**

```javascript
function stableStringify(value) {
  if (value === null || typeof value !== 'object') return JSON.stringify(value);
  if (Array.isArray(value)) return '[' + value.map(stableStringify).join(',') + ']';
  return '{' + Object.keys(value).sort().map(key =>
    JSON.stringify(key) + ':' + stableStringify(value[key])
  ).join(',') + '}';
}
```

**Explanation:** Sort object keys before stringifying so equivalent objects produce the same string.

### 99. Calculate a cart total with discounts and tax.

**Solution:**

```javascript
function calculateCartTotal(items, taxRate = 0) {
  const subtotal = items.reduce((sum, item) => {
    const discount = item.discount || 0;
    return sum + item.price * item.quantity * (1 - discount);
  }, 0);
  return Math.round(subtotal * (1 + taxRate) * 100) / 100;
}
```

**Explanation:** Multiply price and quantity, apply item discounts, add tax, and round to two decimals.

### 100. Validate an object against a simple schema.

**Solution:**

```javascript
function validate(schema, data) {
  const errors = [];
  for (const [key, type] of Object.entries(schema)) {
    if (typeof data[key] !== type) errors.push(key + ' must be ' + type);
  }
  return { valid: errors.length === 0, errors };
}
```

**Explanation:** Check each expected field type and return a structured validation result.

## Reference Docs

- [MDN JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
- [MDN JavaScript Reference](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference)
