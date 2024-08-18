# N_Queens Solver 🏰

Welcome to the **N_Queens Solver**! This Java program tackles the classic N-Queens puzzle, where the challenge is to place `n` queens on an `n x n` chessboard such that no two queens can attack each other.

## 📋 Features

- Solves the N-Queens problem for any board size `n`.
- Prints all possible solutions to the console.
- Counts and displays the number of valid configurations.

## 🛠️ How to Use

### Installation

1. Clone this repository:
   ```bash
   git clone https://github.com/yourusername/N_Queens.git
public class N_Queens {
    public static void main(String[] args) {
        int n = 4; // Size of the chessboard
        boolean[][] board = new boolean[n][n]; // Initialize the board
        int solutionCount = Queens(board, 0); // Solve the puzzle and count solutions
        System.out.println("Total solutions: " + solutionCount); // Print the count
    }

    static int Queens(boolean[][] board, int row) {
        if (row == board.length) {
            display(board); // Display the board configuration
            System.out.println();
            return 1; // Found a valid solution
        }
        int count = 0;
        for (int col = 0; col < board.length; col++) {
            if (isSafe(board, row, col)) {
                board[row][col] = true;
                count += Queens(board, row + 1);
                board[row][col] = false;
            }
        }
        return count;
    }

    private static boolean isSafe(boolean[][] board, int row, int col) {
        // vertical check
        for (int i = 0; i < row; i++) {
            if (board[i][col]) {
                return false;
            }
        }
        // left diagonal
        for (int i = 1; i <= row && col - i >= 0; i++) {
            if (board[row - i][col - i]) {
                return false;
            }
        }
        // right diagonal
        for (int i = 1; i <= row && col + i < board.length; i++) {
            if (board[row - i][col + i]) {
                return false;
            }
        }
        return true;
    }

    private static void display(boolean[][] board) {
        for (boolean[] row : board) {
            for (boolean element : row) {
                System.out.print(element ? "Q " : "X ");
            }
            System.out.println();
        }
    }
}
