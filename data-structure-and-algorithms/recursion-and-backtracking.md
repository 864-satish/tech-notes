# 📖 Recursion and Backtracking
Recursion and backtracking are both important concepts in computer science, and while they are closely related, they are used to solve different types of problems and have distinct characteristics.
Here's a detailed explanation of each:

## 🚀 Recursion
**Definition**: Recursion is a technique in which a function calls itself directly or indirectly to solve a problem.
Each recursive call works on a smaller instance of the same problem until it reaches a base case, which stops the recursion.

**Key Characteristics:**

- Base Case: The condition under which the recursion stops. Without a base case, the recursion would continue indefinitely, leading to a stack overflow.
- Recursive Case: The part of the function where the function calls itself with a smaller or simpler input.
- Simplification: Each recursive call should simplify the problem, moving it closer to the base case.

Example: A simple example is calculating the factorial of a number.
```TypeScript
function factorial(n) {
  if (n === 0) {
    return 1; // Base case
  }
  return n * factorial(n - 1); // Recursive case
}

console.log(factorial(5)); // Output: 120
```

## 🚀 Backtracking

**Definition:** Backtracking is an algorithmic technique for solving problems incrementally by trying partial solutions and then abandoning them if they are not suitable (i.e., if they do not lead to a valid solution). It is often used in combination with recursion.

**Key Characteristics:**

- Trial and Error: Backtracking tries out different solutions, abandoning a path as soon as it determines that this path cannot lead to a valid solution.
- State Reversal: Before abandoning a path, backtracking reverses the last decision made (backtracks) and tries another path.
- Efficiency: Backtracking can be more efficient than simple brute-force solutions because it eliminates large portions of the search space through early termination.

Example: A classic example is solving the N-Queens problem, where you need to place N queens on an N×N chessboard so that no two queens threaten each other.
```TypeScript
function solveNQueens(n) {
  const board = Array.from({ length: n }, () => Array(n).fill('.'));
  const res = [];

  const isSafe = (board, row, col) => {
    for (let i = 0; i < row; i++) {
      if (board[i][col] === 'Q') return false;
    }
    for (let i = row - 1, j = col - 1; i >= 0 && j >= 0; i--, j--) {
      if (board[i][j] === 'Q') return false;
    }
    for (let i = row - 1, j = col + 1; i >= 0 && j < n; i--, j++) {
      if (board[i][j] === 'Q') return false;
    }
    return true;
  };

  const solve = (row) => {
    if (row === n) {
      res.push(board.map((r) => r.join('')));
      return;
    }
    for (let col = 0; col < n; col++) {
      if (isSafe(board, row, col)) {
        board[row][col] = 'Q';
        solve(row + 1);
        board[row][col] = '.'; // Backtrack
      }
    }
  };

  solve(0);
  return res;
}

console.log(solveNQueens(4));

```

## 🚀 Differences between Recursion and Backtracking

- Nature: Recursion is a general problem-solving technique, while backtracking is a specific algorithmic technique often implemented using recursion.
- Purpose: Recursion simplifies a problem by breaking it into smaller subproblems, while backtracking is used to solve constraint satisfaction problems by exploring possible solutions and abandoning paths that do not lead to valid solutions.
- State Management: Backtracking explicitly involves keeping track of the state and undoing decisions (backtracking), whereas recursion involves breaking down problems without necessarily backtracking.

## summary
- Recursion is a method of solving problems by breaking them into smaller subproblems, while backtracking is a specific technique that uses recursion to explore possible solutions and abandon them when they are not feasible.
