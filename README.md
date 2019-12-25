# py-sudoku

A simple Python program that generates and solves m x n Sudoku puzzles.

## Install

```sh
# Python 2
pip install pysudoku

# Python 3
pip3 install pysudoku
```

## Usage

### Basic usage

```py
from sudoku import Sudoku
# Initializes a Sudoku puzzle with 3 x 3 sub-grid and
# generates a puzzle with half of the cells empty
puzzle = Sudoku(3).difficulty(0.5)
puzzle.show()
# +-------+-------+-------+
# | 4 1   | 3     | 7 6   |
# |   9 3 |   7   | 4   1 |
# | 2     | 1 4   |   8 3 |
# +-------+-------+-------+
# | 9 5 8 |       |     7 |
# | 3 4   |     7 |   1   |
# |   7 2 | 8 9 3 | 5 4   |
# +-------+-------+-------+
# |   8   | 2     | 3 7 4 |
# |     4 |       | 1 9 5 |
# |       |   5   | 6     |
# +-------+-------+-------+

solution = puzzle.solve()
solution.show()
# +-------+-------+-------+
# | 4 1 5 | 3 8 9 | 7 6 2 |
# | 8 9 3 | 6 7 2 | 4 5 1 |
# | 2 6 7 | 1 4 5 | 9 8 3 |
# +-------+-------+-------+
# | 9 5 8 | 4 1 6 | 2 3 7 |
# | 3 4 6 | 5 2 7 | 8 1 9 |
# | 1 7 2 | 8 9 3 | 5 4 6 |
# +-------+-------+-------+
# | 5 8 9 | 2 6 1 | 3 7 4 |
# | 6 2 4 | 7 3 8 | 1 9 5 |
# | 7 3 1 | 9 5 4 | 6 2 8 |
# +-------+-------+-------+
```

### Creating puzzles

m x n rectangular puzzles can be initialized using the `Sudoku(width)` or `Sudoku(width, height)` constructors.

```py
# Initializes a 3 x 5 puzzle
puzzle = Sudoku(3, 5)
# Initializes a 4 x 4 puzzle
puzzle = Sudoku(4)
puzzle = Sudoku(4, 4)
```

Use ```solve()``` to get a solved puzzle, or ```difficulty(x)``` to create a problem.

```py
# Create a 3 x 5 sub-grid problem with 0.4 difficulty (40% of cells empty)
puzzle = Sudoku(3, 5).difficulty(0.4)

# Create a solved 4 x 4 problem
puzzle = Sudoku(4).solve()
```

### Displaying puzzles

```py
solution = Sudoku(5, 3).solve()

# Shows the puzzle only
solution.show()
# +----------------+----------------+----------------+
# | 09 10 11 04 06 | 05 01 03 12 13 | 08 14 15 02 07 |
# | 03 05 07 08 01 | 02 14 15 09 04 | 06 10 11 12 13 |
# | 12 02 13 14 15 | 07 10 06 11 08 | 01 03 04 05 09 |
# +----------------+----------------+----------------+
# | 13 14 06 11 08 | 15 07 09 02 12 | 10 01 05 03 04 |
# | 10 03 15 05 02 | 13 04 08 14 01 | 12 09 07 11 06 |
# | 01 07 04 09 12 | 03 05 10 06 11 | 13 02 08 15 14 |
# +----------------+----------------+----------------+
# | 07 13 08 15 05 | 12 11 04 10 03 | 14 06 09 01 02 |
# | 06 01 12 03 09 | 08 02 07 15 14 | 11 13 10 04 05 |
# | 04 11 10 02 14 | 06 09 01 13 05 | 15 08 12 07 03 |
# +----------------+----------------+----------------+
# | 08 12 02 06 10 | 01 13 11 05 07 | 03 04 14 09 15 |
# | 05 15 09 13 11 | 14 03 12 04 10 | 02 07 06 08 01 |
# | 14 04 01 07 03 | 09 06 02 08 15 | 05 11 13 10 12 |
# +----------------+----------------+----------------+
# | 11 09 03 12 13 | 10 15 14 07 02 | 04 05 01 06 08 |
# | 15 06 14 01 04 | 11 08 05 03 09 | 07 12 02 13 10 |
# | 02 08 05 10 07 | 04 12 13 01 06 | 09 15 03 14 11 |
# +----------------+----------------+----------------+


# Use print or show_full to display more information
print(solution)
solution.show_full()
# ---------------------------
# 15x15 (5x3) SUDOKU PUZZLE
# Difficulty: SOLVED
# ---------------------------
# +----------------+----------------+----------------+
# | 09 10 11 04 06 | 05 01 03 12 13 | 08 14 15 02 07 |
# | 03 05 07 08 01 | 02 14 15 09 04 | 06 10 11 12 13 |
# | 12 02 13 14 15 | 07 10 06 11 08 | 01 03 04 05 09 |
# +----------------+----------------+----------------+
# | 13 14 06 11 08 | 15 07 09 02 12 | 10 01 05 03 04 |
# | 10 03 15 05 02 | 13 04 08 14 01 | 12 09 07 11 06 |
# | 01 07 04 09 12 | 03 05 10 06 11 | 13 02 08 15 14 |
# +----------------+----------------+----------------+
# | 07 13 08 15 05 | 12 11 04 10 03 | 14 06 09 01 02 |
# | 06 01 12 03 09 | 08 02 07 15 14 | 11 13 10 04 05 |
# | 04 11 10 02 14 | 06 09 01 13 05 | 15 08 12 07 03 |
# +----------------+----------------+----------------+
# | 08 12 02 06 10 | 01 13 11 05 07 | 03 04 14 09 15 |
# | 05 15 09 13 11 | 14 03 12 04 10 | 02 07 06 08 01 |
# | 14 04 01 07 03 | 09 06 02 08 15 | 05 11 13 10 12 |
# +----------------+----------------+----------------+
# | 11 09 03 12 13 | 10 15 14 07 02 | 04 05 01 06 08 |
# | 15 06 14 01 04 | 11 08 05 03 09 | 07 12 02 13 10 |
# | 02 08 05 10 07 | 04 12 13 01 06 | 09 15 03 14 11 |
# +----------------+----------------+----------------+
```

### Seeds

Problems can be generated with a certain seed.

```py
# Generates a 3x2 puzzle with a given seed
Sudoku(3, 2, seed=100).solve().show()
# +-------+-------+
# | 5 6 3 | 1 2 4 |
# | 2 1 4 | 5 3 6 |
# +-------+-------+
# | 1 5 2 | 6 4 3 |
# | 3 4 6 | 2 5 1 |
# +-------+-------+
# | 6 3 5 | 4 1 2 |
# | 4 2 1 | 3 6 5 |
# +-------+-------+

```

### Importing boards

Puzzle boards can also be imported.

```py
board = [
    [0,0,7,0,4,0,0,0,0],
    [0,0,0,0,0,8,0,0,6],
    [0,4,1,0,0,0,9,0,0],
    [0,0,0,0,0,0,1,7,0],
    [0,0,0,0,0,6,0,0,0],
    [0,0,8,7,0,0,2,0,0],
    [3,0,0,0,0,0,0,0,0],
    [0,0,0,1,2,0,0,0,0],
    [8,6,0,0,7,0,0,0,5]
]
puzzle = Sudoku(3, 3, board=board)

print(puzzle)
# ---------------------------
# 9x9 (3x3) SUDOKU PUZZLE
# Difficulty: 0.74
# ---------------------------
# +-------+-------+-------+
# |     7 |   4   |       |
# |       |     8 |     6 |
# |   4 1 |       | 9     |
# +-------+-------+-------+
# |       |       | 1 7   |
# |       |     6 |       |
# |     8 | 7     | 2     |
# +-------+-------+-------+
# | 3     |       |       |
# |       | 1 2   |       |
# | 8 6   |   7 0 |     5 |
# +-------+-------+-------+

puzzle.solve().show_full()
# ---------------------------
# 9x9 (3x3) SUDOKU PUZZLE
# Difficulty: SOLVED
# ---------------------------
# +-------+-------+-------+
# | 9 8 7 | 6 4 2 | 5 3 1 |
# | 2 3 5 | 9 1 8 | 7 4 6 |
# | 6 4 1 | 5 3 7 | 9 8 2 |
# +-------+-------+-------+
# | 5 2 6 | 3 8 4 | 1 7 9 |
# | 1 7 3 | 2 9 6 | 8 5 4 |
# | 4 9 8 | 7 5 1 | 2 6 3 |
# +-------+-------+-------+
# | 3 1 9 | 8 6 5 | 4 2 7 |
# | 7 5 4 | 1 2 3 | 6 9 8 |
# | 8 6 2 | 4 7 9 | 3 1 5 |
# +-------+-------+-------+
```

### Invalid boards

Invalid boards give errors when attempted to be solved.

```py
board = [
    [0,0,7,0,4,0,0,0,0],
    [0,0,0,0,0,8,0,0,6],
    [0,4,1,0,0,0,9,0,0],
    [0,0,0,0,0,0,1,7,0],
    [0,0,0,0,0,6,0,0,0],
    [0,0,8,7,0,0,2,0,0],
    [3,0,0,0,0,0,0,0,0],
    [0,0,0,1,2,0,0,0,0],
    [8,6,0,0,7,6,0,0,5]
]
puzzle = Sudoku(3, 3, board=board)

puzzle.show_full()
# ---------------------------
# 9x9 (3x3) SUDOKU PUZZLE
# Difficulty: 0.74
# ---------------------------
# +-------+-------+-------+
# |     7 |   4   |       |
# |       |     8 |     6 |
# |   4 1 |       | 9     |
# +-------+-------+-------+
# |       |       | 1 7   |
# |       |     6 |       |
# |     8 | 7     | 2     |
# +-------+-------+-------+
# | 3     |       |       |
# |       | 1 2   |       |
# | 8 6   |   7 6 |     5 |
# +-------+-------+-------+

puzzle.solve().show_full()
# ---------------------------
# 9x9 (3x3) SUDOKU PUZZLE
# Difficulty: INVALID PUZZLE (GIVEN PUZZLE HAS NO SOLUTION)
# ---------------------------
# +-------+-------+-------+
# |       |       |       |
# |       |       |       |
# |       |       |       |
# +-------+-------+-------+
# |       |       |       |
# |       |       |       |
# |       |       |       |
# +-------+-------+-------+
# |       |       |       |
# |       |       |       |
# |       |       |       |
# +-------+-------+-------+
```
