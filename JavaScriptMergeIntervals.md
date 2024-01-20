# JavaScript Merge Intervals
<br/>

## Challenge
Given an array of `intervals` where `intervals[i] = [starti, endi]`, merge all overlapping intervals, and return an array of the non-overlapping intervals that cover all the intervals in the input.
<br/>
<br/>

### 1<sup>st</sup> Example

```JavaScript
Input: intervals = [[1,3],[2,6],[8,10],[15,18]]
Output: [[1,6],[8,10],[15,18]]
Explanation: Since intervals [1,3] and [2,6]
             overlap, merge them into [1,6].
```

### 2<sup>nd</sup> Example

```JavaScript
Input: intervals = [[1,4],[4,5]]
Output: [[1,5]]
Explanation: Intervals [1,4] and [4,5]
             are considered overlapping.
```

<br/>

### Constraints

- `1 <= intervals.length <= 10⁴`
- `intervals[i].length == 2`
- `0 <= starti <= endi <= 10⁴`

<br/>

## Solution

```JavaScript
const merge = (intervals) => {
    intervals.sort((a, b) => a[0] - b[0]);

    let i = 0;

    while (i < intervals.length - 1) {
        const [_, firstRight]           = intervals[i],
              [secondLeft, secondRight] = intervals[i + 1];

        if (firstRight >= secondLeft) {
            intervals[i][1] = Math.max(firstRight, secondRight);
            intervals.splice(i + 1, 1);
        } else {
            i++;
        }
    }

    return intervals;
};
```

<br/>

## Explanation

I've coded a function called `merge` that takes an array of intervals as input and returns the merged intervals.
<br/>

The function starts by sorting the `intervals` array in ascending order based on the first element of each interval. This is done using the `sort` method and a comparator function that compares the first elements of two intervals.
<br/>

A variable `i` is initialized to `0`, which will be used as an index to iterate through the `intervals` array.
<br/>

The function enters a `while` loop that will continue until `i` reaches the second-to-last index of the `intervals` array.
<br/>

Inside the loop, the current interval and the next interval are extracted and assigned to variables using destructuring assignment. The first element of the current interval is ignored (assigned to `_`), and the second element is assigned to `firstRight`. The first element of the next interval is assigned to `secondLeft`, and the second element is assigned to `secondRight`.
<br/>

A conditional statement checks if the `firstRight` value is greater than or equal to the `secondLeft` value. This condition determines if the two intervals can be merged.
<br/>

If the condition is true, the function updates the end value of the current interval to the maximum of `firstRight` and `secondRight` using the `Math.max` function. This effectively merges the two intervals.
<br/>

The `splice` method is used to remove the next interval from the `intervals` array, starting from the index `i+1`. This is done to eliminate the duplicate interval that was merged.
<br/>

If the condition in the previous step is false, meaning the two intervals cannot be merged, the function increments the index `i` by `1` to move to the next pair of intervals.
<br/>

After the while loop finishes, the modified `intervals` array is returned as the result of the function.
<br/>

In summary, this function merges overlapping intervals in the input array. It sorts the intervals based on the start values and then iterates through the sorted array, merging intervals when necessary. The resulting merged intervals are returned as the output of the function.
<br/>
<br/>
<br/>
<br/>

### :next_track_button: [Next (Valid Anagram)][Next]
<br/>

### :previous_track_button: [Previous (Sort Method Overview)][Previous]
<br/>

### :play_or_pause_button: [More Sorting Challenges][More]
<br/>

### :eject_button: [Return to Course Outline][Return]
<br/>

[Next]: https://github.com/Superklok/JavaScriptSorting/blob/main/JavaScriptValidAnagram.md
[Previous]: https://github.com/Superklok/JavaScriptSorting/blob/main/JavaScriptArraySortMethodOverview.md
[More]: https://github.com/Superklok/JavaScriptSorting
[Return]: https://github.com/Superklok/LearnJavaScript