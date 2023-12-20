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

## Explanation:

I've defined a function called `arrayPairSum` that takes an array of numbers, `nums`, as input. The purpose of this function is to calculate the sum of the minimum of each pair of numbers in the array and return the total sum.
<br/>

Inside the function, a variable called `result` is initialized to 0. This variable will store the sum of the minimum of each pair.
<br/>

The input array `nums` is sorted in ascending order using the `sort` method and a compare function. This ensures that the smaller numbers come before the larger numbers in the array.
<br/>

A `for` loop is used to iterate over the sorted `nums` array. The loop runs from `i = 0` to `i < nums.length` with an increment of `2` in each iteration. This ensures that we only consider every second number in the array, which represents the minimum of each pair.
<br/>

Within the loop, the current number `nums[i]` (which represents the minimum of the pair) is added to the `result` variable.
<br/>

After the loop finishes, the final value of `result`, which represents the sum of the minimum of each pair in the array, is returned as the output of the function.
<br/>

In summary, this function calculates the sum of the minimum of each pair of numbers in the input array. It achieves this by sorting the array and then iterating over it, adding the minimum of each pair to a running total. The final total is returned as the output of the function.
<br/>
<br/>