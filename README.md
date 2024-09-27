# Question-2
Question 2: DSA Given an array of integers nums and an integer target, return the indices of the two numbers such that they add up to target. You may assume that each input would have exactly one solution, and you may not use the same element twice. You can return the answer in any order.

For example, given:

const nums = [2, 7, 11, 15];

const target = 9;

The function should return [0, 1] because nums[0] + nums[1] = 2 + 7 = 9.

# Solution

```
const twoSumTarget = (nums, target) => {
  
  // Check if target is a number
  if (typeof target !== 'number') {
    throw new Error("Target number must be a number.");
  }
  
  // Check if number is an array and has atleat 2 elements
  if (!Array.isArray(nums) || nums.length < 2) {
    throw new Error("Provided input must be an array with at least two numbers.");
  }

  // Create a hash map to store the numbers and their indices
  const numMap = new Map();

  for (let i = 0; i < nums.length; i++) {
    const complement = target - nums[i];

    // Check if the complement exists in the hash map
    if (numMap.has(complement)) {
      return [numMap.get(complement), i];
    }

    numMap.set(nums[i], i);
  }

  // If no target sum is found, throw an error
  throw new Error("No two numbers add up to the target.");
}


try {
  const nums = [2, 7, 11, 15];
  const target = 18;
  const result = twoSumTarget(nums, target);
  console.log(result);
} catch (error) {
  console.error(error.message);
}
```
