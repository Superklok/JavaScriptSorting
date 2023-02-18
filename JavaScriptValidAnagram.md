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