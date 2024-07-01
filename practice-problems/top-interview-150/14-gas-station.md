# 134. Gas Station

## Leetcode Problem
https://leetcode.com/problems/gas-station/description/?envType=study-plan-v2&envId=top-interview-150

## Problem Understanding
You are given two arrays `gas` and `cost`, both of length `n`. Each `gas[i]` represents the amount of gas available at station `i`, and each `cost[i]` represents the cost of gas required to travel from station `i` to the next station `(i + 1)`. The stations are arranged in a circular route.

Your task is to determine the starting station index from which you can complete the circuit once in a clockwise direction. If no such starting station exists, return -1. If a solution exists, it is guaranteed to be unique.

### Example
Example 1:
```
Input: gas = [1,2,3,4,5], cost = [3,4,5,1,2]
Output: 3
```
Explanation:
```
Start at station 3 (index 3), gas available: 4, cost to next: 1
Travel to station 4: tank = 4 - 1 + 5 = 8
Travel to station 0: tank = 8 - 2 + 1 = 7
Travel to station 1: tank = 7 - 3 + 2 = 6
Travel to station 2: tank = 6 - 4 + 3 = 5
Travel back to station 3: tank = 5 - 5 + 4 = 4
```
Example 2:
```
Input: gas = [2,3,4], cost = [3,4,3]
Output: -1
```
Explanation:
- Starting at any station does not provide enough gas to complete the circuit.
### Constraints
- n == gas.length == cost.length
- 1 <= n <= 105
- 0 <= gas[i], cost[i] <= 104

## Approach
The problem can be solved in `O(n)` time complexity using a `greedy approach`:

- **Total Gas vs. Total Cost:** First, check if the total amount of gas is greater than or equal to the total cost. If not, it's impossible to complete the circuit, and we return -1.
- **Greedy Approach:** If it's possible to complete the circuit, use a greedy approach to find the starting station. Keep track of the current tank balance while traversing the stations. If the balance drops below zero, the next station becomes the new starting point, and reset the balance.

## Solution Code
```javascript
var canCompleteCircuit = function(gas, cost) {
    let totalGas=0, totalCost=0, tank=0, start=0;

    for(let i=0;i<gas.length;i++){
        totalGas+=gas[i];
        totalCost+=cost[i];
        tank += gas[i] - cost[i];
        if(tank<0){
            start=i+1;
            tank=0
        }
    }

    return totalGas >= totalCost ? start : -1;
};

// Example usage:
console.log(canCompleteCircuit([1,2,3,4,5], [3,4,5,1,2])); // Output: 3
console.log(canCompleteCircuit([2,3,4], [3,4,3])); // Output: -1
```

## Explanation of Code
#### 1. Initialization:
- `totalGas` and `totalCost` keep track of the total gas available and the total cost required to complete the circuit.
- `tank` keeps track of the current gas balance.
- `start` is the potential starting station index.
#### 2. Loop through stations:
- Add the gas and cost of the current station to `totalGas` and `totalCost`.
- Update `tank` with the net gas balance at the current station (`gas[i] - cost[i]`).
- If `tank` drops below zero, it means the current starting point isn't feasible, so set the next station as the new starting point and reset `tank` to zero.
#### 3. Check feasibility:
- After the loop, if `totalGas` is greater than or equal to `totalCost`, return the `start` index.
- Otherwise, return `-1` since it's not possible to complete the circuit.

## Complexity Analysis
- **Time Complexity:** `O(n)`, where n is the length of the gas array. This is because we only traverse the `gas` and `cost` arrays once.
- **Space Complexity:** `O(1)`, since we use a constant amount of extra space regardless of the input size.
