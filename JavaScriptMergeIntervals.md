# JavaScript Merge Intervals

## Challenge:

Given an array of `intervals` where `intervals[i] = [starti, endi]`, merge all overlapping intervals, and return an array of the non-overlapping intervals that cover all the intervals in the input.

### 1<sup>st</sup> Example:

`Input: intervals = [[1,3],[2,6],[8,10],[15,18]]`
<br/>
`Output: [[1,6],[8,10],[15,18]]`
<br/>
`Explanation: Since intervals [1,3] and [2,6] overlap, merge them into [1,6].`

### 2<sup>nd</sup> Example:

`Input: intervals = [[1,4],[4,5]]`
<br/>
`Output: [[1,5]]`
<br/>
`Explanation: Intervals [1,4] and [4,5] are considered overlapping.`

### Constraints:

`1 <= intervals.length <= 10⁴`
<br/>
`intervals[i].length == 2`
<br/>
`0 <= starti <= endi <= 10⁴`

## Solution:

`const merge = (intervals) => {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`intervals.sort((a, b) => a[0] - b[0]);`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`let i = 0;`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`while (i < intervals.length - 1) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`const [_, firstRight]           = intervals[i],`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`[secondLeft, secondRight] = intervals[i + 1];`
<br/>
<br/>   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`if (firstRight >= secondLeft) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`intervals[i][1] = Math.max(firstRight, secondRight);`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`intervals.splice(i + 1, 1);`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`} else {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`i++;`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`return intervals;`
<br/>
`};`
<br/>
<br/>

## Explanation:

I've coded a function called `merge` that takes an array of intervals as input and returns the merged intervals.
<br/>

The function starts by sorting the intervals array in ascending order based on the first element of each interval. This is done using the `sort` method and a comparator function that compares the first elements of two intervals.
<br/>

A variable `i` is initialized to`, which will be used as an index to iterate through the intervals array.
<br/>

The function enters a `while` loop that will continue until `i` reaches the second-to-last index of the intervals array.
<br/>

Inside the loop, the current interval and the next interval are extracted and assigned to variables using destructuring assignment. The first element of the current interval is ignored (assigned to `_`), and the second element is assigned to `firstRight`. The first element of the next interval is assigned to `secondLeft`, and the second element is assigned to `secondRight`.
<br/>

A conditional statement checks if the `firstRight` value is greater than or equal to the `secondLeft` value. This condition determines if the two intervals can be merged.
<br/>

If the condition is true, the function updates the end value of the current interval to the maximum of `firstRight` and `secondRight` using the `Math.max` function. This effectively merges the two intervals.
<br/>

The `splice` method is used to remove the next interval from the intervals array, starting from the index `i+1`. This is done to eliminate the duplicate interval that was merged.
<br/>

If the condition in the previous step is false, meaning the two intervals cannot be merged, the function increments the index `i` by 1 to move to the next pair of intervals.
<br/>

After the while loop finishes, the modified intervals array is returned as the result of the function.
<br/>

In summary, this function merges overlapping intervals in the input array. It sorts the intervals based on the start values and then iterates through the sorted array, merging intervals when necessary. The resulting merged intervals are returned as the output of the function.
<br/>
<br/>