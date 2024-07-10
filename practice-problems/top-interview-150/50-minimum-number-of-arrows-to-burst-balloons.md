# 452. Minimum Number of Arrows to Burst Balloons

## Leetcode Problem
https://leetcode.com/problems/minimum-number-of-arrows-to-burst-balloons/description/?envType=study-plan-v2&envId=top-interview-150

## Approach
To solve the problem of finding the minimum number of arrows required to burst all balloons on a flat wall represented by intervals `[xstart, xend]`, we can use a `greedy algorithm approach`. Here's how it can be approached:

### Explanation
1. Sorting Intervals:
    - First, sort the intervals based on their `xend` values. This is because shooting an arrow at the end of the balloon's horizontal diameter ensures that the arrow can burst all balloons that it touches.
2. Greedy Strategy:
    - Initialize `end` to minus infinity (`-Infinity`) to keep track of the end of the current arrow shot.
    - Initialize `arrows` to `0`, which counts the number of arrows shot.
3. Iterate through Intervals:
    - For each balloon interval `[xstart, xend]`:
        - If the current `xstart` is greater than `end`, it means a new arrow is needed because the current arrow cannot burst this balloon. Therefore, increment the `arrows` count and update `end` to `xend`.
        - If `xstart` is within the range `[end, xend]`, it means the balloon can be burst by the current arrow, so no additional arrow is needed. Only update `end` to `xend`.
4. Return Result:
    - After iterating through all intervals, arrows will contain the minimum number of arrows needed to burst all balloons.

## Solution Code
```javascript
var findMinArrowShots = function(points) {
    if (points.length === 0) return 0;
    
    // Sort intervals by their end points
    points.sort((a, b) => a[1] - b[1]);
    
    let arrows = 0;
    let end = -Infinity;
    
    for (let point of points) {
        let xstart = point[0];
        let xend = point[1];
        
        if (xstart > end) {
            // Need a new arrow because current balloon is not covered by the previous arrow
            arrows++;
            end = xend;
        } else {
            // Current balloon can be covered by the previous arrow
            // No need to increment arrows count
            end = Math.min(end, xend);
        }
    }
    
    return arrows;
};

// Example usage:
console.log(findMinArrowShots([[10,16],[2,8],[1,6],[7,12]])); // Output: 2
console.log(findMinArrowShots([[1,2],[3,4],[5,6],[7,8]])); // Output: 4
console.log(findMinArrowShots([[1,2],[2,3],[3,4],[4,5]])); // Output: 2
```

## Complexity Analysis
### Time Complexity:
- Sorting the intervals takes `O(n log n)` time.
- Iterating through the sorted intervals takes `O(n)` time.
- Therefore, the overall time complexity is `O(n log n)` due to the sorting step dominating.
### Space Complexity:
- The space complexity is `O(1)` since we are using a constant amount of extra space for variables (`arrows`, `end`), and not using any additional data structures that scale with input size.
### Conclusion
This approach efficiently finds the minimum number of arrows required to burst all balloons by leveraging `sorting and a greedy strategy` based on the balloon intervals' end points. It ensures optimal performance within the given constraints, making it suitable for large inputs.
