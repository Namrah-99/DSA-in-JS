# 121. Best Time to Buy and Sell Stock

## Leetcode Problem
https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/?envType=study-plan-v2&envId=top-interview-150

## Problem Explanation
The problem at hand is to find the maximum profit that can be achieved by buying and then selling a single stock at different days within an array of stock prices. Here’s a breakdown of how to approach and solve this problem:

#### Problem Understanding
You are given an array `prices` where `prices[i]` represents the price of a stock on the `i-th` day. The goal is to:

- Buy the stock on one day (`prices[j]` where `j` is the index of the day you buy).
- Sell the stock on a future day (`prices[k]` where `k` is the index of the day you sell).
- Maximize the profit (`prices[k] - prices[j]`), ensuring that `k > j` (you can't sell before you buy).

If no profitable transaction is possible, return `0`.

## Approach
To solve this problem efficiently, you can use a single pass through the array while keeping track of the minimum price encountered so far (`min_price`) and updating the maximum profit (`max_profit`) accordingly:

##### 1. Initialize Variables:
  - `min_price` to a very large number (`Infinity`) to track the lowest price encountered so far.
  - `max_profit` to `0` initially, as no profit is made yet.

##### 2. Iterate Through the Array:
  - For each price in the `prices` array:
    - Update `min_price` if the current price is lower than `min_price`.
    - Update `max_profit` if the difference between the current price and `min_price` (`price - min_price`) is greater than `max_profit`.

##### 3. Return the Result:
  - After iterating through the array, `max_profit` will contain the maximum profit achievable from a single buy-sell transaction.

## Example Walkthrough
```
Input: prices = [7, 1, 5, 3, 6, 4]

min_price = Infinity
max_profit = 0

Iterating through prices:
- price = 7
  min_price = 7, max_profit = 0
- price = 1
  min_price = 1, max_profit = max(0, 1 - 7) = -6 (but max_profit should never go below 0)
- price = 5
  min_price = 1, max_profit = max(0, 5 - 1) = 4
- price = 3
  min_price = 1, max_profit = max(4, 3 - 1) = 4
- price = 6
  min_price = 1, max_profit = max(4, 6 - 1) = 5
- price = 4
  min_price = 1, max_profit = max(5, 4 - 1) = 5

Return max_profit = 5
```

## Solution Code
```javascript
var maxProfit = function (prices) {
    let min_price = Infinity;
    let max_profit = 0;
    for (let i = 0; i < prices.length; i++) {
        max_profit = Math.max(max_profit, prices[i] - min_price);
        min_price = Math.min(min_price, prices[i]);
    }
    return max_profit
};
// Example usage:
console.log(maxProfit([7,1,5,3,6,4])); // output: 5
```

## Complexity Analysis
- Time Complexity: `O(n)`, where n is the length of the `prices` array. We make a single pass through the array.
- Space Complexity: `O(1)`. We use only a constant amount of extra space for variables (`min_price` and `max_profit`).
