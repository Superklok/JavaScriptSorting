# JavaScript Valid Anagram

## Challenge:

Given two strings `s` and `t`, return true if `t` is an anagram of `s`, and `false` otherwise.

An anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

### 1<sup>st</sup> Example:

`Input: s = "anagram", t = "nagaram"`
<br/>
`Output: true`

### 2<sup>nd</sup> Example:

`Input: s = "rat", t = "car"`
<br/>
`Output: false`

### Constraints:

`1 <= s.length, t.length <= 5 * 10⁴`
<br/>
`s` and `t` consist of lowercase English letters.

## Solution:

`const isAnagram = (s, t) => {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`s = s.split("").sort().join();`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`t = t.split("").sort().join();`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`return s === t;`
<br/>
`};`
<br/>
<br/>

## Explanation:

I've created a function called `isAnagram` that takes in two strings, `s` and `t`, as parameters. The purpose of this function is to check if the two strings are anagrams of each other.
<br/>

Inside the function, the first string `s` is split into an array of individual characters using the `split("")` method. Similarly, the second string `t` is also split into an array of characters.
<br/>

The `sort()` method is then applied to both arrays to sort the characters in alphabetical order. This ensures that the characters in both strings are arranged in the same order for comparison.
<br/>

Next, the `join()` method is used to join the sorted arrays back into strings. This recreates the original strings with the characters in sorted order.
<br/>

Finally, the two sorted and joined strings, `s` and `t`, are compared using the strict equality operator (`===`). If the two strings are identical, it means that they have the same characters in the same order, indicating that they are anagrams. In this case, the function returns `true`. Otherwise, it returns `false` to indicate that the strings are not anagrams.
<br/>

In summary, this function checks if two input strings are anagrams by sorting the characters in each string and comparing the sorted strings. If the sorted strings are identical, the function returns `true`, indicating that the strings are anagrams. Otherwise, it returns `false`.
<br/>
<br/>