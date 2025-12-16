# 1. Introduction
Code review is a systematic examination of source code with the goal of improving its quality, readability, maintainability, and correctness. In software engineering, readable and well-structured code is especially important because it allows other developers, instructors, and even the original author to understand, debug, and extend the program more easily.
This report reviews a JavaScript-based implementation of the classic Tetris game using an HTML <canvas>. The focus of this review is on Code Readability and Structure, while also evaluating the program’s logic, input handling, replayability, user experience, use of constants, and efficiency.

# 2. Code Readability and Structure 
## 2.1 Overall Organization
**The code is well organized within a single HTML file that contains:**

- HTML structure

- CSS styling

- JavaScript game logic


From a learning and demonstration perspective, this structure is acceptable and common for small projects. The JavaScript logic is placed inside a <script> tag at the bottom of the HTML file, which ensures the DOM is loaded before the script runs. This improves readability and avoids execution issues.
However, for better structure and scalability, separating JavaScript into an external .js file and separating the Css in to its  own files would improve maintainability and align with software engineering best practices. 


## 2.2 Naming Conventions
Most variable and function names are clear, descriptive, and meaningful, which significantly improves readability.
Examples:
- boardRows, boardColumns, tileSize


- initializeBoard()


- getRandomTetromino()


- isTetrominoColliding()


- drawBoard() and drawTetromino()


These names clearly describe what each variable or function does, making the code easy to follow even for someone reading it for the first time.
Minor issues:


Some variable names mix singular and plural meanings (e.g., randomTetromino vs currentTetromino), which may slightly confuse beginners.


Overall, the naming quality is very good .
## 2.3 Indentation and Formatting
The code uses consistent indentation and spacing throughout:
+ Nested loops are clearly aligned


+ Functions are visually separated


+ Braces {} are used consistently


This makes the control flow easy to understand and reduces cognitive load when reading loops and conditionals. The consistent formatting reflects good programming discipline.
## 2.4 Use of Comments
The code contains frequent and meaningful comments, which greatly enhances readability.
Examples:
- // initialize the board


- // game loop


- // function to clear lines and make above lines fall down


- // keydown listener


Comments explain why something is done, not just what is done, which is especially valuable in an educational setting.
One improvement would be to reduce comments that simply restate the code (e.g., “// move tetromino down”) and instead focus on explaining logic or intent.

## 2.5 Modularity and Function Design
The program is well modularized:
- Each function has a single responsibility


- Rendering, logic, and input handling are separated


- The game loop (update) is clearly defined


- Functions are kept reasonably short and readable, which aligns well with good software engineering principles. 
