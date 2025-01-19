# JavaScript Closure Issue in setTimeout Loop

This repository demonstrates a common JavaScript closure issue encountered when using `setTimeout` within a loop. The problem arises because the `setTimeout` callbacks don't capture the value of `i` at the time they are created; instead, they capture a reference to the variable `i`. By the time the callbacks execute, the loop has already completed, and `i` is equal to its final value (10).

The `bug.js` file contains the buggy code. The `bugSolution.js` file provides a solution using an immediately invoked function expression (IIFE) to create a new scope for each iteration of the loop, ensuring that each callback captures the correct value of `i`.

## Bug
The issue occurs because of how closures work in JavaScript.  The callback function within `setTimeout` closes over the variable `i`, not its value at the time of creation. When the `setTimeout` finally executes, the loop has already finished, and `i` is 10. Therefore, all the `console.log` statements print 10.

## Solution
The solution uses an immediately invoked function expression (IIFE) to create a new scope for each iteration. This ensures that each callback has its own copy of `i`, preserving the correct value at the time of the `setTimeout` call.