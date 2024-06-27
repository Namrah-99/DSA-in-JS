# 2410. Maximum Matching of Players with Trainers

## Leetcode Problem
https://leetcode.com/problems/maximum-matching-of-players-with-trainers/description/

## Approach
To solve this problem efficiently, we can use a `greedy approach` and `two-pointers approach` along with `sorting`. The idea is to match players with trainers in such a way that we maximize the number of matches by always trying to pair the smallest available player ability with the smallest available trainer capacity that can accommodate that player. Here’s how we can do it step-by-step:

## Approach
#### 1. Sort both arrays:
  - Sort the `players` array in ascending order of abilities.
  - Sort the `trainers` array in ascending order of training capacities.
#### 2. Use two pointers:
  - Initialize two pointers, one for the `players` array (`i`) and one for the `trainers` array (`j`), both starting at 0.
  - Iterate through both arrays and try to match the current player with the current trainer.
#### 3. Greedy Matching:
  - If the current player's ability is less than or equal to the current trainer's capacity, it means we can match them. Increment both pointers and increase the match count.
  - If the current player's ability is greater than the current trainer's capacity, increment the trainer pointer to find a suitable trainer.
#### 4. End of Iteration:
  - The iteration ends when we have gone through either all players or all trainers.
  - The count of matches will give the maximum number of matchings possible.

## Solution Code
```javascript
var matchPlayersAndTrainers = function(players, trainers) {
    // Sort both arrays
    players.sort((a,b)=> a-b);
    trainers.sort((a,b)=> a-b);
    // Pointers for players and trainers
    let i=0,j=0; let matches = 0;

    // Use two pointers to find the maximum number of matchings
    while(i<players.length && j<trainers.length){
        if(players[i] <= trainers[j]){
            matches++; // Match found
            i++; // Move o next player
            j++; // Move to next trainer
        }else{
            // Trainer cannot accommodate the player, so move to next trainer 
            j++;
        }
    }
    // Return maximum number of matchings between players and trainers 
    return matches
};

// Example Usage
let players1 = [4, 7, 9];
let trainers1 = [8, 2, 5, 8];
console.log(matchPlayersAndTrainers(players1, trainers1)); // Output: 2

let players2 = [1, 1, 1];
let trainers2 = [10];
console.log(matchPlayersAndTrainers(players2, trainers2)); // Output: 1
```

## Time Complexity
- Sorting both arrays takes O(nlogn) time.
- The two-pointer iteration through both arrays takes O(n) time.
- Therefore, the overall time complexity is `O(nlogn)`.
