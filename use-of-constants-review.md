# Use of Constants 

## Overview
This review examines the use of constants in the Tetris game code. Constants are fixed values that do not change during runtime and help improve code readability, maintainability, and scalability.

## Board and Display Constants
Key board and rendering values are correctly defined as constants:
- Board rows
- Board columns
- Tile size
Using named constants instead of hard-coded values avoids magic numbers and makes the purpose of each value immediately clear.

## Canvas Scaling
The canvas dimensions are calculated using board and tile constants. This ensures that all rendering logic remains consistent and allows the board size or tile size to be changed easily from a single location.
This demonstrates good design practice and thoughtful use of constants.

## Tetromino Definitions
All tetromino shapes and their associated colors are stored in a constant data structure. This centralizes game data and separates it from the game logic.
This approach improves organization and makes it easier to modify or extend the game in the future.

## Areas for Improvement
Some values are still hard-coded and could be converted into constants for improved clarity and maintainability, such as:

- Normal drop speed
- Fast drop speed
- Initial tetromino spawn position
Defining these values as named constants would further reduce duplication and improve flexibility.

## Conclusion
The code demonstrates good use of constants, particularly for board configuration and tetromino data. While a few hard-coded values remain, the overall implementation reflects solid programming practice and an understanding of the importance of constants.
