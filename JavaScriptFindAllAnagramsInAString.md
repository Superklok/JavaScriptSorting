# JavaScript Find All Anagrams In A String

## Challenge:

Given two strings `s` and `p`, return an array of all the start indices of `p`'s anagrams in `s`. You may return the answer in any order.

An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

### 1<sup>st</sup> Example:

`Input: s = "cbaebabacd", p = "abc"`
<br/>
`Output: [0,6]`
<br/>
`Explanation: The substring with start index = 0 is "cba", which is an anagram of "abc".`
<br/>
`The substring with start index = 6 is "bac", which is an anagram of "abc".`

### 2<sup>nd</sup> Example:

`Input: s = "abab", p = "ab"`
<br/>
`Output: [0,1,2]`
<br/>
`Explanation: The substring with start index = 0 is "ab", which is an anagram of "ab".`
<br/>
`The substring with start index = 1 is "ba", which is an anagram of "ab".`
<br/>
`The substring with start index = 2 is "ab", which is an anagram of "ab".`

### Constraints:

`1 <= s.length, p.length <= 3 * 10⁴`
<br/>
`s` and `p` consist of lowercase English letters.

## Solution:

`const findAnagrams = (s, p) => {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`const output      = [],`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`neededChars = {};`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`for (let char of p) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`if (char in neededChars) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`neededChars[char]++;`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`} else neededChars[char] = 1;`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`let left  = 0,`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`right = 0,` 
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`count = p.length;` 
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`while (right < s.length) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`if (neededChars[s[right]] > 0) count--;`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`neededChars[s[right]]--;`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`right++;`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`if (count === 0) output.push(left);`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`if (right - left == p.length) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`if (neededChars[s[left]] >= 0) count++;`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`neededChars[s[left]]++;`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`left++;`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`return output;`
<br/>
`};`
<br/>
<br/>

## Explanation:

I've built a function called `findAnagrams` that takes in two parameters, `s` and `p`. The purpose of this function is to find all the anagrams of string  `p`  in string  `s`  and return an array of indices where the anagrams start in `s`.
<br/>

This function begins by initializing an empty array called `output` and an empty object called `neededChars`. The `output` array will store the indices of the anagrams found, while the `neededChars` object will keep track of the characters needed to form an anagram.
<br/>

Next, the function iterates through each character `char` in string `p`. For each character, it checks if `char` already exists as a key in `neededChars`. If it does, the value associated with that key is incremented by 1. If `char` does not exist as a key, it is added to `neededChars` with a value of 1.
<br/>

After initializing some variables (`left`, `right`, and `count`) to control a sliding window approach, the function enters a while loop that continues until the `right` pointer reaches the end of string `s`.
<br/>

Within the loop, it checks if the count of the character at `s[right]` in `neededChars` is greater than 0. If it is, the `count` variable is decremented. The count of the character at `s[right]` in  `neededChars`  is also decremented. The  `right`  pointer is then incremented to move the sliding window to the right.
<br/>

If the count variable becomes 0, it means an anagram is found. In this case, the current value of `left` is added to the `output` array.
<br/>

If the size of the sliding window (determined by `right - left`) becomes equal to the length of string `p`, it means we need to shrink the window from the left. In this case, the function checks if the count of the character at `s[left]` in `neededChars` is greater than or equal to 0. If it is, the `count` variable is incremented. The count of the character at `s[left]` in `neededChars` is also incremented. The `left` pointer is then incremented to move the sliding window to the right.
<br/>

Finally, this function returns the `output` array containing the indices where the anagrams start in `s`.
<br/>
<br/>