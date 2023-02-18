# JavaScript Array Partition

## Challenge:

Given an integer array `nums` of `2n` integers, group these integers into `n` pairs `(a₁, b₁), (a₂, b₂), ..., (aₙ, bₙ)` such that the sum of `min(aᵢ, bᵢ)` for all `i` is maximized. Return the maximized sum.

### 1<sup>st</sup> Example:

`Input: nums = [1,4,3,2]`
<br/>
`Output: 4`
<br/>
`Explanation: All possible pairings (ignoring the ordering of elements) are:`
<br/>
`1. (1, 4), (2, 3) -> min(1, 4) + min(2, 3) = 1 + 2 = 3`
<br/>
`2. (1, 3), (2, 4) -> min(1, 3) + min(2, 4) = 1 + 2 = 3`
<br/>
`3. (1, 2), (3, 4) -> min(1, 2) + min(3, 4) = 1 + 3 = 4`
<br/>
`So the maximum possible sum is 4.`

### 2<sup>nd</sup> Example:

`Input: nums = [6,2,6,5,1,2]`
<br/>
`Output: 9`
<br/>
`Explanation: The optimal pairing is (2, 1), (2, 5), (6, 6). min(2, 1) + min(2, 5) + min(6, 6) = 1 + 2 + 6 = 9.`

### Constraints:

`1 <= n <= 10⁴`
<br/>
`nums.length == 2 * n`
<br/>
`-10⁴ <= nums[i] <= 10⁴`

## Solution:

`const arrayPairSum = (nums) => {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`let result = 0;`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`nums.sort(function(a, b){return a-b});`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`for(let i = 0; i < nums.length; i = i+2){`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`result += nums[i];`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`return result;`
<br/>
`};`
<br/>
<br/>