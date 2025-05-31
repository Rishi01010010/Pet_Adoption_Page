Two Sum - LeetCode #1
1. Problem Statement
Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target. You may assume that each input would have exactly one solution, and you may not use the same element twice. You can return the answer in any order.
2. Solution (Code in Java)
class Solution {
    public int[] twoSum(int[] nums, int target) {
        HashMap<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            int complement = target - nums[i];
            if (map.containsKey(complement)) {
                return new int[] { map.get(complement), i };
            }
            map.put(nums[i], i);
        }
        return new int[] {}; // No solution found
    }
}

3. Approach
The approach uses a HashMap to store the numbers and their indices as we iterate through the array. For each number, we calculate its complement (target - current number) and check if it exists in the HashMap. If found, we return the indices of the complement and the current number. If not, we add the current number and its index to the HashMap.
4. Logic

Initialize an empty HashMap to store numbers as keys and their indices as values.
Iterate through the array.
For each element nums[i], compute the complement (target - nums[i]).
Check if the complement exists in the HashMap:
If yes, return the index of the complement (from HashMap) and the current index i.
If no, add the current number nums[i] and its index i to the HashMap.


If no solution is found, return an empty array.

5. Pattern Used
Hash Table (HashMap) pattern: This problem leverages a HashMap to achieve O(n) time complexity by trading off space for speed, allowing constant-time lookups for the complement.
6. Test Case
Input: nums = [2, 7, 11, 15], target = 9Output: [0, 1]Explanation: nums[0] + nums[1] = 2 + 7 = 9, so the indices [0, 1] are returned.
7. Dry Runs
Dry Run 1
Input: nums = [2, 7, 11, 15], target = 9  

Initialize: map = {}
Step 1: i = 0, nums[0] = 2, complement = 9 - 2 = 7
map does not contain 7, add 2 -> 0 to map. Now, map = {2: 0}


Step 2: i = 1, nums[1] = 7, complement = 9 - 7 = 2
map contains 2, return [map.get(2), 1] = [0, 1]


Output: [0, 1]

Dry Run 2
Input: nums = [3, 2, 4], target = 6  

Initialize: map = {}
Step 1: i = 0, nums[0] = 3, complement = 6 - 3 = 3
map does not contain 3, add 3 -> 0 to map. Now, map = {3: 0}


Step 2: i = 1, nums[1] = 2, complement = 6 - 2 = 4
map does not contain 4, add 2 -> 1 to map. Now, map = {3: 0, 2: 1}


Step 3: i = 2, nums[2] = 4, complement = 6 - 4 = 2
map contains 2, return [map.get(2), 2] = [1, 2]


Output: [1, 2]

