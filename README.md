# Express.js Route Handler Missing Error Handling

This repository demonstrates a common error in Express.js route handlers: the lack of proper error handling for invalid input.  Specifically, the `/users/:id` route doesn't handle cases where `:id` is not a valid number.  This can lead to unexpected crashes or unexpected behavior.

## Bug

The `bug.js` file contains the buggy code.  It attempts to parse the `userId` as an integer without checking if it's a valid integer.  If a non-numeric ID is provided, `parseInt(userId)` will return `NaN`, and the subsequent `users.find` operation will fail silently or throw an error, causing the server to crash or return an unexpected response.

## Solution

The `bugSolution.js` file provides a corrected version of the code.  It includes explicit error handling to check if `userId` is a number before attempting to parse and use it.  This ensures that the server responds gracefully with a 404 error if an invalid ID is provided.

## How to reproduce

1. Clone this repository.
2. Navigate to the directory.
3. Run `npm install express` to install the required dependencies.
4. Run `node bug.js` and try accessing `/users/abc` or `/users/123`.
5. Compare the behavior of the buggy and corrected versions.
