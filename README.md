include <stdio.h>
#include <stdbool.h>

bool isValid(char** board, int row, int col, char k) {
    for (int i = 0; i < 9; i++) {
        if (board[row][i] == k) {
            return false;
        }
    }
    for (int i = 0; i < 9; i++) {
        if (board[i][col] == k) {
            return false;
        }
    }
    int RowStart = row - row % 3;
    int ColStart = col - col % 3;
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            if (board[RowStart + i [ColStart + j] == k) {
                return false;
            }
        }
    }
    return true;
}
bool solve(char** board) {
    for (int i = 0; i < 9; i++) {
        for (int j = 0; j < 9; j++) {
            if (board[i][j] == '.') {
                for (char k = '1'; k <= '9'; k++) {
                    if (isValid(board, i, j, k)) {
                        board[i][j] = k;
                        if (solve(board)) {
                            return true;
                        }
                        board[i][j] = '.';
                    }
                }
                return false;
            }
        }
    }
    return true; 
}

void Sudoku(char** board, int boardSize, int* boardColSize) {
    solve(board);
}

int main() {
    char* board[9] = {
        "53..7....",
        "6..195...",
        ".98....6.",
        "8...6...3",
        "4..8.3..1",
        "7...2...6",
        ".6....28.",
        "...419..5",
        "....8..79"
    };
    char board2[9][9];
    for (int i = 0; i < 9; i++) {
        for (int j = 0; j < 9; j++) {
            board2[i][j] = board[i][j];
        }
    }
    char* boardPtr[9];
    for (int i = 0; i < 9; i++) {
        boardPtr[i] = board2[i];
    }
    int board3[9] = {9, 9, 9, 9, 9, 9, 9, 9, 9};
    int Size = 9;  
    Sudoku(boardPtr, Size, board3);

  printf("Solution:\n");
    for (int i = 0; i < 9; i++) {
        for (int j = 0; j < 9; j++) {
            printf("%c ", board2[i][j]);
        }
        printf("\n");
    }

   return 0;
}
