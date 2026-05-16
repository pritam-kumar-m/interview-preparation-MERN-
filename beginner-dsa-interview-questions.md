# Beginner-Level DSA Interview Questions with Solutions and Explanations

Prepared for beginner-friendly DSA revision using JavaScript solutions. The problems are grouped by topic instead of difficulty because this file is intentionally beginner-level.

**Question count:** 100

## Arrays

### 1. Find the sum of all elements in an array.

**Solution:**

```javascript
function sumArray(arr) {
  return arr.reduce((sum, n) => sum + n, 0);
}
```

**Explanation:** Traverse all elements once and keep adding them to a running total.

### 2. Find the average of array elements.

**Solution:**

```javascript
function average(arr) {
  if (arr.length === 0) return 0;
  return arr.reduce((sum, n) => sum + n, 0) / arr.length;
}
```

**Explanation:** Average is total sum divided by number of elements; handle empty arrays safely.

### 3. Find the largest element in an array.

**Solution:**

```javascript
function largest(arr) {
  let max = arr[0];
  for (const n of arr) if (n > max) max = n;
  return max;
}
```

**Explanation:** Compare every element with the current maximum.

### 4. Find the smallest element in an array.

**Solution:**

```javascript
function smallest(arr) {
  let min = arr[0];
  for (const n of arr) if (n < min) min = n;
  return min;
}
```

**Explanation:** Compare every element with the current minimum.

### 5. Find the second largest unique element.

**Solution:**

```javascript
function secondLargest(arr) {
  let first = -Infinity, second = -Infinity;
  for (const n of arr) {
    if (n > first) { second = first; first = n; }
    else if (n > second && n !== first) second = n;
  }
  return second === -Infinity ? null : second;
}
```

**Explanation:** Track the largest and second largest values in one pass.

### 6. Reverse an array without using reverse().

**Solution:**

```javascript
function reverseArray(arr) {
  const result = [];
  for (let i = arr.length - 1; i >= 0; i--) result.push(arr[i]);
  return result;
}
```

**Explanation:** Read values from the end and push them into a new array.

### 7. Check whether an array is sorted in ascending order.

**Solution:**

```javascript
function isSorted(arr) {
  for (let i = 1; i < arr.length; i++) {
    if (arr[i] < arr[i - 1]) return false;
  }
  return true;
}
```

**Explanation:** Every element should be greater than or equal to the previous element.

### 8. Remove duplicates from a sorted array.

**Solution:**

```javascript
function removeDuplicatesSorted(arr) {
  const result = [];
  for (const n of arr) {
    if (result.length === 0 || result[result.length - 1] !== n) result.push(n);
  }
  return result;
}
```

**Explanation:** Because the array is sorted, duplicates appear together, so compare with the last added value.

### 9. Count positive, negative, and zero values.

**Solution:**

```javascript
function countTypes(arr) {
  const count = { positive: 0, negative: 0, zero: 0 };
  for (const n of arr) {
    if (n > 0) count.positive++;
    else if (n < 0) count.negative++;
    else count.zero++;
  }
  return count;
}
```

**Explanation:** Classify each number and increment the matching counter.

### 10. Rotate an array right by one position.

**Solution:**

```javascript
function rotateRightOne(arr) {
  if (arr.length <= 1) return arr;
  return [arr[arr.length - 1], ...arr.slice(0, -1)];
}
```

**Explanation:** Move the last element to the front and keep the rest in order.

### 11. Rotate an array left by one position.

**Solution:**

```javascript
function rotateLeftOne(arr) {
  if (arr.length <= 1) return arr;
  return [...arr.slice(1), arr[0]];
}
```

**Explanation:** Move the first element to the end.

### 12. Find the missing number from 1 to n.

**Solution:**

```javascript
function missingNumber(arr, n) {
  const expected = n * (n + 1) / 2;
  const actual = arr.reduce((sum, x) => sum + x, 0);
  return expected - actual;
}
```

**Explanation:** Use the arithmetic series sum formula and subtract the actual sum.

### 13. Find the first duplicate value.

**Solution:**

```javascript
function firstDuplicate(arr) {
  const seen = new Set();
  for (const n of arr) {
    if (seen.has(n)) return n;
    seen.add(n);
  }
  return null;
}
```

**Explanation:** A Set lets us check whether a value has appeared before.

### 14. Merge two arrays.

**Solution:**

```javascript
function mergeArrays(a, b) {
  return [...a, ...b];
}
```

**Explanation:** Spread both arrays into a new array.

### 15. Move all zeroes to the end.

**Solution:**

```javascript
function moveZeroes(arr) {
  const nonZero = arr.filter(n => n !== 0);
  return [...nonZero, ...Array(arr.length - nonZero.length).fill(0)];
}
```

**Explanation:** Keep non-zero values in order, then append zeroes.

### 16. Search an element using linear search.

**Solution:**

```javascript
function linearSearch(arr, target) {
  for (let i = 0; i < arr.length; i++) {
    if (arr[i] === target) return i;
  }
  return -1;
}
```

**Explanation:** Check each element until the target is found.

### 17. Build a prefix sum array.

**Solution:**

```javascript
function prefixSum(arr) {
  const result = [];
  let sum = 0;
  for (const n of arr) {
    sum += n;
    result.push(sum);
  }
  return result;
}
```

**Explanation:** Each prefix value stores the sum from index 0 to the current index.

### 18. Find whether any subarray has a given sum using brute force.

**Solution:**

```javascript
function hasSubarraySum(arr, target) {
  for (let i = 0; i < arr.length; i++) {
    let sum = 0;
    for (let j = i; j < arr.length; j++) {
      sum += arr[j];
      if (sum === target) return true;
    }
  }
  return false;
}
```

**Explanation:** Try every start and end position; this is beginner-friendly but O(n^2).

### 19. Count frequency of numbers in an array.

**Solution:**

```javascript
function numberFrequency(arr) {
  const map = {};
  for (const n of arr) map[n] = (map[n] || 0) + 1;
  return map;
}
```

**Explanation:** Use an object as a frequency table.

### 20. Find leaders in an array.

**Solution:**

```javascript
function leaders(arr) {
  const result = [];
  let maxRight = -Infinity;
  for (let i = arr.length - 1; i >= 0; i--) {
    if (arr[i] > maxRight) { result.push(arr[i]); maxRight = arr[i]; }
  }
  return result.reverse();
}
```

**Explanation:** A leader is greater than all elements to its right; scan from right to left.

## Strings

### 21. Reverse a string.

**Solution:**

```javascript
function reverseString(str) {
  let result = '';
  for (let i = str.length - 1; i >= 0; i--) result += str[i];
  return result;
}
```

**Explanation:** Append characters from the end to the beginning.

### 22. Check whether a string is a palindrome.

**Solution:**

```javascript
function isPalindrome(str) {
  let left = 0, right = str.length - 1;
  while (left < right) {
    if (str[left++] !== str[right--]) return false;
  }
  return true;
}
```

**Explanation:** Compare characters from both ends moving toward the center.

### 23. Count vowels and consonants.

**Solution:**

```javascript
function countVowelsConsonants(str) {
  const result = { vowels: 0, consonants: 0 };
  for (const ch of str.toLowerCase()) {
    if (/[a-z]/.test(ch)) 'aeiou'.includes(ch) ? result.vowels++ : result.consonants++;
  }
  return result;
}
```

**Explanation:** Ignore non-letters, then classify each letter.

### 24. Count frequency of each character.

**Solution:**

```javascript
function charFrequency(str) {
  const freq = {};
  for (const ch of str) freq[ch] = (freq[ch] || 0) + 1;
  return freq;
}
```

**Explanation:** Each character becomes a key in the frequency object.

### 25. Remove spaces from a string.

**Solution:**

```javascript
function removeSpaces(str) {
  return str.replace(/\s/g, '');
}
```

**Explanation:** The regex removes all whitespace characters.

### 26. Check whether two strings are anagrams.

**Solution:**

```javascript
function areAnagrams(a, b) {
  return a.split('').sort().join('') === b.split('').sort().join('');
}
```

**Explanation:** Anagrams have the same sorted character sequence.

### 27. Find the first non-repeating character.

**Solution:**

```javascript
function firstNonRepeating(str) {
  const freq = charFrequency(str);
  for (const ch of str) if (freq[ch] === 1) return ch;
  return null;
}
```

**Explanation:** Count all characters first, then return the first with frequency 1.

### 28. Find the most frequent character.

**Solution:**

```javascript
function mostFrequentChar(str) {
  const freq = charFrequency(str);
  let best = null;
  for (const ch in freq) if (best === null || freq[ch] > freq[best]) best = ch;
  return best;
}
```

**Explanation:** Build a frequency map and select the character with the highest count.

### 29. Count uppercase and lowercase letters.

**Solution:**

```javascript
function countCase(str) {
  const result = { upper: 0, lower: 0 };
  for (const ch of str) {
    if (/[A-Z]/.test(ch)) result.upper++;
    if (/[a-z]/.test(ch)) result.lower++;
  }
  return result;
}
```

**Explanation:** Use letter-range checks to classify characters.

### 30. Replace all occurrences of a character.

**Solution:**

```javascript
function replaceChar(str, from, to) {
  return str.split(from).join(to);
}
```

**Explanation:** Splitting by the old character and joining with the new one replaces all occurrences.

### 31. Reverse the words in a sentence.

**Solution:**

```javascript
function reverseWords(sentence) {
  return sentence.trim().split(/\s+/).reverse().join(' ');
}
```

**Explanation:** Split into words, reverse word order, and join with spaces.

### 32. Find the longest word in a sentence.

**Solution:**

```javascript
function longestWord(sentence) {
  return sentence.split(/\s+/).reduce((best, word) => word.length > best.length ? word : best, '');
}
```

**Explanation:** Keep the longest word while scanning.

### 33. Compress repeated characters.

**Solution:**

```javascript
function compressString(str) {
  let result = '', count = 1;
  for (let i = 0; i < str.length; i++) {
    if (str[i] === str[i + 1]) count++;
    else { result += str[i] + count; count = 1; }
  }
  return result;
}
```

**Explanation:** Count consecutive equal characters and append character plus count.

### 34. Check whether one string is a subsequence of another.

**Solution:**

```javascript
function isSubsequence(s, t) {
  let i = 0;
  for (const ch of t) if (ch === s[i]) i++;
  return i === s.length;
}
```

**Explanation:** Move through the larger string and match characters in order.

### 35. Count occurrences of a substring.

**Solution:**

```javascript
function countSubstring(str, sub) {
  let count = 0, index = 0;
  while ((index = str.indexOf(sub, index)) !== -1) {
    count++; index += sub.length;
  }
  return count;
}
```

**Explanation:** Repeatedly search from the next position after each match.

## Hashing

### 36. Solve two sum using a hash map.

**Solution:**

```javascript
function twoSum(nums, target) {
  const map = new Map();
  for (let i = 0; i < nums.length; i++) {
    const need = target - nums[i];
    if (map.has(need)) return [map.get(need), i];
    map.set(nums[i], i);
  }
  return [];
}
```

**Explanation:** Store previous numbers so each complement lookup is O(1).

### 37. Find intersection of two arrays.

**Solution:**

```javascript
function intersection(a, b) {
  const setB = new Set(b);
  return [...new Set(a)].filter(x => setB.has(x));
}
```

**Explanation:** Set lookup makes membership checking fast.

### 38. Find union of two arrays.

**Solution:**

```javascript
function union(a, b) {
  return [...new Set([...a, ...b])];
}
```

**Explanation:** A Set naturally removes duplicates.

### 39. Find the first duplicate using Set.

**Solution:**

```javascript
function firstDuplicate(arr) {
  const seen = new Set();
  for (const x of arr) {
    if (seen.has(x)) return x;
    seen.add(x);
  }
  return null;
}
```

**Explanation:** Return the first value that already exists in the set.

### 40. Count pairs with a given sum.

**Solution:**

```javascript
function countPairs(nums, target) {
  const freq = new Map();
  let count = 0;
  for (const n of nums) {
    count += freq.get(target - n) || 0;
    freq.set(n, (freq.get(n) || 0) + 1);
  }
  return count;
}
```

**Explanation:** For each number, count how many earlier complements have appeared.

### 41. Check whether all characters are unique.

**Solution:**

```javascript
function hasUniqueChars(str) {
  return new Set(str).size === str.length;
}
```

**Explanation:** A Set removes duplicates, so size should match string length.

### 42. Check whether two strings are isomorphic.

**Solution:**

```javascript
function isIsomorphic(a, b) {
  if (a.length !== b.length) return false;
  const mapA = new Map(), mapB = new Map();
  for (let i = 0; i < a.length; i++) {
    if ((mapA.has(a[i]) && mapA.get(a[i]) !== b[i]) || (mapB.has(b[i]) && mapB.get(b[i]) !== a[i])) return false;
    mapA.set(a[i], b[i]); mapB.set(b[i], a[i]);
  }
  return true;
}
```

**Explanation:** Maintain one-to-one mappings in both directions.

### 43. Group anagrams.

**Solution:**

```javascript
function groupAnagrams(words) {
  const groups = new Map();
  for (const word of words) {
    const key = word.split('').sort().join('');
    if (!groups.has(key)) groups.set(key, []);
    groups.get(key).push(word);
  }
  return [...groups.values()];
}
```

**Explanation:** Words with the same sorted characters belong to the same group.

### 44. Find common elements in three arrays.

**Solution:**

```javascript
function commonThree(a, b, c) {
  const setB = new Set(b), setC = new Set(c);
  return [...new Set(a)].filter(x => setB.has(x) && setC.has(x));
}
```

**Explanation:** Use sets for the second and third arrays, then filter unique values from the first.

### 45. Find majority element using a map.

**Solution:**

```javascript
function majorityElement(nums) {
  const limit = Math.floor(nums.length / 2);
  const freq = new Map();
  for (const n of nums) {
    const count = (freq.get(n) || 0) + 1;
    if (count > limit) return n;
    freq.set(n, count);
  }
  return null;
}
```

**Explanation:** A majority element appears more than n/2 times.

## Searching and Sorting

### 46. Binary search in a sorted array.

**Solution:**

```javascript
function binarySearch(arr, target) {
  let left = 0, right = arr.length - 1;
  while (left <= right) {
    const mid = Math.floor((left + right) / 2);
    if (arr[mid] === target) return mid;
    arr[mid] < target ? left = mid + 1 : right = mid - 1;
  }
  return -1;
}
```

**Explanation:** Compare with the middle and discard half of the search space.

### 47. Find lower bound index.

**Solution:**

```javascript
function lowerBound(arr, target) {
  let left = 0, right = arr.length;
  while (left < right) {
    const mid = Math.floor((left + right) / 2);
    if (arr[mid] < target) left = mid + 1;
    else right = mid;
  }
  return left;
}
```

**Explanation:** Lower bound is the first index where value is greater than or equal to target.

### 48. Implement selection sort.

**Solution:**

```javascript
function selectionSort(arr) {
  arr = [...arr];
  for (let i = 0; i < arr.length; i++) {
    let min = i;
    for (let j = i + 1; j < arr.length; j++) if (arr[j] < arr[min]) min = j;
    [arr[i], arr[min]] = [arr[min], arr[i]];
  }
  return arr;
}
```

**Explanation:** Repeatedly select the smallest remaining element and place it at the front.

### 49. Implement bubble sort.

**Solution:**

```javascript
function bubbleSort(arr) {
  arr = [...arr];
  for (let i = 0; i < arr.length; i++) {
    for (let j = 0; j < arr.length - i - 1; j++) {
      if (arr[j] > arr[j + 1]) [arr[j], arr[j + 1]] = [arr[j + 1], arr[j]];
    }
  }
  return arr;
}
```

**Explanation:** Swap adjacent out-of-order elements until larger values bubble to the end.

### 50. Implement insertion sort.

**Solution:**

```javascript
function insertionSort(arr) {
  arr = [...arr];
  for (let i = 1; i < arr.length; i++) {
    const key = arr[i];
    let j = i - 1;
    while (j >= 0 && arr[j] > key) arr[j + 1] = arr[j--];
    arr[j + 1] = key;
  }
  return arr;
}
```

**Explanation:** Insert each element into its correct position in the sorted left part.

### 51. Merge two sorted arrays.

**Solution:**

```javascript
function mergeSorted(a, b) {
  const result = [];
  let i = 0, j = 0;
  while (i < a.length && j < b.length) result.push(a[i] <= b[j] ? a[i++] : b[j++]);
  return result.concat(a.slice(i), b.slice(j));
}
```

**Explanation:** Two pointers merge values in increasing order.

### 52. Find kth smallest element.

**Solution:**

```javascript
function kthSmallest(arr, k) {
  return [...arr].sort((a, b) => a - b)[k - 1];
}
```

**Explanation:** For beginner interviews, sorting first is simple; more advanced solutions use heaps or quickselect.

### 53. Count occurrences of a value in sorted array.

**Solution:**

```javascript
function countOccurrencesSorted(arr, target) {
  const first = lowerBound(arr, target);
  const afterLast = lowerBound(arr, target + 1);
  return afterLast - first;
}
```

**Explanation:** For numbers, lower bounds find the first target and first value after target.

### 54. Find search insert position.

**Solution:**

```javascript
function searchInsert(arr, target) {
  return lowerBound(arr, target);
}
```

**Explanation:** The lower bound is exactly where the target should be inserted.

### 55. Sort an array containing only 0, 1, and 2.

**Solution:**

```javascript
function sort012(arr) {
  const count = [0, 0, 0];
  for (const n of arr) count[n]++;
  return [
    ...Array(count[0]).fill(0),
    ...Array(count[1]).fill(1),
    ...Array(count[2]).fill(2)
  ];
}
```

**Explanation:** Count each value, then rebuild the sorted array.

### 56. Find floor of a target in sorted array.

**Solution:**

```javascript
function floorValue(arr, target) {
  let ans = null;
  for (const n of arr) {
    if (n <= target) ans = n;
    else break;
  }
  return ans;
}
```

**Explanation:** Floor is the greatest value less than or equal to the target.

### 57. Find ceil of a target in sorted array.

**Solution:**

```javascript
function ceilValue(arr, target) {
  for (const n of arr) if (n >= target) return n;
  return null;
}
```

**Explanation:** Ceil is the smallest value greater than or equal to the target.

### 58. Find a peak element.

**Solution:**

```javascript
function peakElement(arr) {
  for (let i = 0; i < arr.length; i++) {
    if ((i === 0 || arr[i] >= arr[i - 1]) && (i === arr.length - 1 || arr[i] >= arr[i + 1])) return arr[i];
  }
  return null;
}
```

**Explanation:** A peak is not smaller than its neighbors.

### 59. Square a sorted array and keep it sorted.

**Solution:**

```javascript
function sortedSquares(arr) {
  return arr.map(n => n * n).sort((a, b) => a - b);
}
```

**Explanation:** A beginner solution squares values and sorts the result.

### 60. Sort strings by length.

**Solution:**

```javascript
function sortByLength(words) {
  return [...words].sort((a, b) => a.length - b.length);
}
```

**Explanation:** Compare string lengths in the sort comparator.

## Stack and Queue

### 61. Implement a stack using an array.

**Solution:**

```javascript
class Stack {
  constructor() { this.items = []; }
  push(x) { this.items.push(x); }
  pop() { return this.items.pop(); }
  peek() { return this.items[this.items.length - 1]; }
}
```

**Explanation:** A stack follows LIFO: last in, first out.

### 62. Implement a queue using an array.

**Solution:**

```javascript
class Queue {
  constructor() { this.items = []; }
  enqueue(x) { this.items.push(x); }
  dequeue() { return this.items.shift(); }
  front() { return this.items[0]; }
}
```

**Explanation:** A queue follows FIFO: first in, first out.

### 63. Check balanced parentheses.

**Solution:**

```javascript
function isBalanced(str) {
  const stack = [];
  const pairs = { ')': '(', ']': '[', '}': '{' };
  for (const ch of str) {
    if ('([{'.includes(ch)) stack.push(ch);
    if (')]}'.includes(ch) && stack.pop() !== pairs[ch]) return false;
  }
  return stack.length === 0;
}
```

**Explanation:** Push opening brackets and match them when closing brackets appear.

### 64. Find next greater element.

**Solution:**

```javascript
function nextGreater(arr) {
  const result = Array(arr.length).fill(-1);
  const stack = [];
  for (let i = 0; i < arr.length; i++) {
    while (stack.length && arr[i] > arr[stack.at(-1)]) result[stack.pop()] = arr[i];
    stack.push(i);
  }
  return result;
}
```

**Explanation:** The stack stores indexes waiting for a greater value to the right.

### 65. Reverse a stack represented as an array.

**Solution:**

```javascript
function reverseStack(stack) {
  const temp = [];
  while (stack.length) temp.push(stack.pop());
  return temp;
}
```

**Explanation:** Popping from the original stack creates reversed order.

### 66. Implement a simple min stack.

**Solution:**

```javascript
class MinStack {
  constructor() { this.stack = []; this.minStack = []; }
  push(x) { this.stack.push(x); this.minStack.push(Math.min(x, this.minStack.at(-1) ?? x)); }
  pop() { this.minStack.pop(); return this.stack.pop(); }
  getMin() { return this.minStack.at(-1); }
}
```

**Explanation:** Keep another stack of current minimum values.

### 67. Implement queue using two stacks.

**Solution:**

```javascript
class QueueUsingStacks {
  constructor() { this.in = []; this.out = []; }
  enqueue(x) { this.in.push(x); }
  dequeue() {
    if (!this.out.length) while (this.in.length) this.out.push(this.in.pop());
    return this.out.pop();
  }
}
```

**Explanation:** Move items from input stack to output stack only when output stack is empty.

### 68. Remove adjacent duplicate characters.

**Solution:**

```javascript
function removeAdjacentDuplicates(str) {
  const stack = [];
  for (const ch of str) stack.at(-1) === ch ? stack.pop() : stack.push(ch);
  return stack.join('');
}
```

**Explanation:** Use a stack and cancel a character when it matches the top.

### 69. Validate expression brackets.

**Solution:**

```javascript
function validBrackets(expr) {
  return isBalanced(expr.replace(/[^()[\]{}]/g, ''));
}
```

**Explanation:** Remove non-bracket characters, then reuse balanced-parentheses logic.

### 70. Implement a circular queue.

**Solution:**

```javascript
class CircularQueue {
  constructor(size) { this.arr = Array(size); this.size = size; this.front = 0; this.count = 0; }
  enqueue(x) { if (this.count === this.size) return false; this.arr[(this.front + this.count++) % this.size] = x; return true; }
  dequeue() { if (!this.count) return undefined; const x = this.arr[this.front]; this.front = (this.front + 1) % this.size; this.count--; return x; }
}
```

**Explanation:** Modulo arithmetic wraps indexes around the fixed-size array.

## Recursion

### 71. Find factorial using recursion.

**Solution:**

```javascript
function factorial(n) {
  if (n <= 1) return 1;
  return n * factorial(n - 1);
}
```

**Explanation:** The base case stops recursion at 1; each call multiplies by the smaller factorial.

### 72. Find Fibonacci using recursion.

**Solution:**

```javascript
function fibonacci(n) {
  if (n <= 1) return n;
  return fibonacci(n - 1) + fibonacci(n - 2);
}
```

**Explanation:** The recursive definition matches Fibonacci, but this simple version is not efficient for large n.

### 73. Find sum from 1 to n.

**Solution:**

```javascript
function sumToN(n) {
  if (n === 0) return 0;
  return n + sumToN(n - 1);
}
```

**Explanation:** Break the problem into n plus the sum before n.

### 74. Return numbers from 1 to n.

**Solution:**

```javascript
function numbersToN(n) {
  if (n === 0) return [];
  return [...numbersToN(n - 1), n];
}
```

**Explanation:** Build the previous list recursively and append n.

### 75. Reverse a string using recursion.

**Solution:**

```javascript
function reverseRecursive(str) {
  if (str.length <= 1) return str;
  return reverseRecursive(str.slice(1)) + str[0];
}
```

**Explanation:** Reverse the substring after the first character, then append the first character.

### 76. Calculate power using recursion.

**Solution:**

```javascript
function power(base, exp) {
  if (exp === 0) return 1;
  return base * power(base, exp - 1);
}
```

**Explanation:** base^exp equals base multiplied by base^(exp-1).

### 77. Find GCD using Euclid algorithm.

**Solution:**

```javascript
function gcd(a, b) {
  if (b === 0) return Math.abs(a);
  return gcd(b, a % b);
}
```

**Explanation:** Euclid algorithm repeatedly replaces the larger problem with the remainder.

### 78. Count digits recursively.

**Solution:**

```javascript
function countDigits(n) {
  n = Math.abs(n);
  if (n < 10) return 1;
  return 1 + countDigits(Math.floor(n / 10));
}
```

**Explanation:** Remove one digit each recursive call by dividing by 10.

### 79. Check palindrome recursively.

**Solution:**

```javascript
function palindromeRecursive(str) {
  if (str.length <= 1) return true;
  if (str[0] !== str[str.length - 1]) return false;
  return palindromeRecursive(str.slice(1, -1));
}
```

**Explanation:** Compare outer characters and recursively check the inner substring.

### 80. Sum an array recursively.

**Solution:**

```javascript
function sumArrayRecursive(arr, index = 0) {
  if (index === arr.length) return 0;
  return arr[index] + sumArrayRecursive(arr, index + 1);
}
```

**Explanation:** Add the current element and recursively sum the rest.

## Linked Lists

### 81. Create a linked list node.

**Solution:**

```javascript
class ListNode {
  constructor(value) {
    this.value = value;
    this.next = null;
  }
}
```

**Explanation:** A singly linked list node stores a value and a pointer to the next node.

### 82. Traverse a linked list.

**Solution:**

```javascript
function traverse(head) {
  const values = [];
  while (head) { values.push(head.value); head = head.next; }
  return values;
}
```

**Explanation:** Move node by node until the pointer becomes null.

### 83. Count nodes in a linked list.

**Solution:**

```javascript
function countNodes(head) {
  let count = 0;
  while (head) { count++; head = head.next; }
  return count;
}
```

**Explanation:** Increment a counter while traversing the list.

### 84. Search a value in a linked list.

**Solution:**

```javascript
function searchList(head, target) {
  while (head) {
    if (head.value === target) return true;
    head = head.next;
  }
  return false;
}
```

**Explanation:** Check each node value until target is found or list ends.

### 85. Insert a node at the head.

**Solution:**

```javascript
function insertHead(head, value) {
  const node = new ListNode(value);
  node.next = head;
  return node;
}
```

**Explanation:** New node points to the old head and becomes the new head.

### 86. Insert a node at the tail.

**Solution:**

```javascript
function insertTail(head, value) {
  const node = new ListNode(value);
  if (!head) return node;
  let current = head;
  while (current.next) current = current.next;
  current.next = node;
  return head;
}
```

**Explanation:** Traverse to the last node and attach the new node.

### 87. Delete the head node.

**Solution:**

```javascript
function deleteHead(head) {
  return head ? head.next : null;
}
```

**Explanation:** The second node becomes the new head.

### 88. Reverse a linked list.

**Solution:**

```javascript
function reverseList(head) {
  let prev = null, current = head;
  while (current) {
    const next = current.next;
    current.next = prev;
    prev = current;
    current = next;
  }
  return prev;
}
```

**Explanation:** Reverse each next pointer while walking through the list.

### 89. Find the middle node.

**Solution:**

```javascript
function middleNode(head) {
  let slow = head, fast = head;
  while (fast && fast.next) {
    slow = slow.next;
    fast = fast.next.next;
  }
  return slow;
}
```

**Explanation:** Fast moves twice as quickly, so slow reaches the middle when fast reaches the end.

### 90. Detect a cycle in a linked list.

**Solution:**

```javascript
function hasCycle(head) {
  let slow = head, fast = head;
  while (fast && fast.next) {
    slow = slow.next;
    fast = fast.next.next;
    if (slow === fast) return true;
  }
  return false;
}
```

**Explanation:** Floyd cycle detection uses slow and fast pointers; if they meet, a cycle exists.

## Trees and Graphs

### 91. Create a binary tree node.

**Solution:**

```javascript
class TreeNode {
  constructor(value) {
    this.value = value;
    this.left = null;
    this.right = null;
  }
}
```

**Explanation:** A binary tree node stores a value and references to left and right children.

### 92. Inorder traversal of a binary tree.

**Solution:**

```javascript
function inorder(root, result = []) {
  if (!root) return result;
  inorder(root.left, result);
  result.push(root.value);
  inorder(root.right, result);
  return result;
}
```

**Explanation:** Inorder visits left subtree, node, then right subtree.

### 93. Preorder traversal of a binary tree.

**Solution:**

```javascript
function preorder(root, result = []) {
  if (!root) return result;
  result.push(root.value);
  preorder(root.left, result);
  preorder(root.right, result);
  return result;
}
```

**Explanation:** Preorder visits node first, then left and right subtrees.

### 94. Postorder traversal of a binary tree.

**Solution:**

```javascript
function postorder(root, result = []) {
  if (!root) return result;
  postorder(root.left, result);
  postorder(root.right, result);
  result.push(root.value);
  return result;
}
```

**Explanation:** Postorder visits children before the node.

### 95. Find height of a binary tree.

**Solution:**

```javascript
function height(root) {
  if (!root) return 0;
  return 1 + Math.max(height(root.left), height(root.right));
}
```

**Explanation:** Tree height is one plus the maximum height of the child subtrees.

### 96. Count nodes in a binary tree.

**Solution:**

```javascript
function countTreeNodes(root) {
  if (!root) return 0;
  return 1 + countTreeNodes(root.left) + countTreeNodes(root.right);
}
```

**Explanation:** Count the current node plus nodes in left and right subtrees.

### 97. Level-order traversal of a tree.

**Solution:**

```javascript
function levelOrder(root) {
  if (!root) return [];
  const result = [], queue = [root];
  while (queue.length) {
    const node = queue.shift();
    result.push(node.value);
    if (node.left) queue.push(node.left);
    if (node.right) queue.push(node.right);
  }
  return result;
}
```

**Explanation:** Use a queue to visit nodes level by level.

### 98. Search a value in a binary search tree.

**Solution:**

```javascript
function searchBST(root, target) {
  while (root) {
    if (root.value === target) return true;
    root = target < root.value ? root.left : root.right;
  }
  return false;
}
```

**Explanation:** Use BST ordering to move left for smaller values and right for larger values.

### 99. Breadth-first search in a graph.

**Solution:**

```javascript
function graphBFS(graph, start) {
  const visited = new Set([start]);
  const queue = [start], order = [];
  while (queue.length) {
    const node = queue.shift();
    order.push(node);
    for (const next of graph[node] || []) {
      if (!visited.has(next)) { visited.add(next); queue.push(next); }
    }
  }
  return order;
}
```

**Explanation:** BFS uses a queue and visits neighbors level by level.

### 100. Depth-first search in a graph.

**Solution:**

```javascript
function graphDFS(graph, start, visited = new Set(), order = []) {
  if (visited.has(start)) return order;
  visited.add(start); order.push(start);
  for (const next of graph[start] || []) graphDFS(graph, next, visited, order);
  return order;
}
```

**Explanation:** DFS explores as far as possible along each path before backtracking.

## Revision Notes

- First understand the brute-force solution, then improve time or space complexity.
- Practice dry runs with small inputs.
- For JavaScript interviews, explain edge cases such as empty arrays, duplicate values, null nodes, and sorted vs unsorted input.
