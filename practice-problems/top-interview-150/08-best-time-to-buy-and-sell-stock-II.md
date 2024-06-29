# 122. Best Time to Buy and Sell Stock II

## Leetcode Problem
https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/description/?envType=study-plan-v2&envId=top-interview-150

## Problem Explanation
The problem is to find the maximum profit you can achieve from a given list of stock prices, where you can buy and sell the stock on any given day, but you can only hold at most one share of the stock at any time. You can also buy and sell on the same day.

The goal is to find the maximum profit by buying and selling the stock **as many times as possible*. The optimal strategy is to sum up all the positive differences between consecutive days, as these represent the profit from each transaction.

## Examples
Example 1:
```
Input: prices = [7,1,5,3,6,4]
Output: 7
Explanation:
Buy on day 2 (price = 1) and sell on day 3 (price = 5), profit = 5-1 = 4.
Buy on day 4 (price = 3) and sell on day 5 (price = 6), profit = 6-3 = 3.
Total profit is 4 + 3 = 7.
```
Example 2:
```
Input: prices = [1,2,3,4,5]
Output: 4
Explanation:
Buy on day 1 (price = 1) and sell on day 5 (price = 5), profit = 5-1 = 4.
Total profit is 4.
```
Example 3:
```
Input: prices = [7,6,4,3,1]
Output: 0
Explanation:
There is no way to make a positive profit, so we never buy the stock to achieve the maximum profit of 0.
```
##### Constraints
- 1 <= prices.length <= 3 * 10^4
- 0 <= prices[i] <= 10^4

## Approach
- Initialize the total profit to 0.
- Iterate through the price array from the second day to the last day.
- If the price on the current day is greater than the price on the previous day, add the difference to the total profit.
- Return the total profit.

## Solution Code
```javascript
var maxProfit = function(prices) {
    let totalProfit = 0;
    
    for (let i = 1; i < prices.length; i++) {
        if (prices[i] > prices[i-1]) {
            totalProfit += prices[i] - prices[i-1];
        }
    }
    
    return totalProfit;
};

// Example usage:
console.log(maxProfit([7, 1, 5, 3, 6, 4])); // Output: 7
console.log(maxProfit([1, 2, 3, 4, 5])); // Output: 4
console.log(maxProfit([7, 6, 4, 3, 1])); // Output: 0
```

## Complexity Analysis
#### Time Complexity
- The time complexity of this solution is `O(n)`, where n is the length of the array. This is because we are making a single pass through the array.
#### Space Complexity
- The space complexity of this solution is `O(1)` as we are using only a few extra variables regardless of the input size.
