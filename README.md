
# 2048

2048 is a popular tile-matching puzzle game. The game is played on a 4x4 grid, and the objective is to combine tiles with the same number to create a tile with the number 2048.





### 

![App Screenshot](https://play-lh.googleusercontent.com/oOoWbtsz8-8aGnysFrDnhbHB1atKwtMUCOvld7U9mJpQuR1naQ0_vZ2maDfAw1R3zQ)




## HTML

- Make file 2048.html in your prefered IDE. 

The basic syntax of HTML should be written.

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    
</body>
</html>

```

Add the CSS link and the JS link that will be used in the project in the <head> tag. 

**CSS**
```
<link rel="stylesheet" href="style.css">
```
**JS LINK**
```
<script src="2048.js"></script>
```

In the body tag, use h1 to display the title "2048" at the top of the game interface.

```
<h1>2048</h1>
```
Use hr for a horizontal rule or line.
It is used to visually separate content on the webpage. In this context, it might be used to separate the title from the game board.

```
<hr>
```

In the next line the score is displayed in a h2 tag, span is used so that the value of the score can be updated in JavaScript. 

```
<h2>Score - <span id="score">0</span></h2>
```

- <div id="board">: This is the main container for the game board. It represents the grid where the game tiles will be placed and moved.

- <div class="icon">: Inside the game board container, there is a nested <div> element with the class "icon." This is used to style or position the game tiles within the grid.

- <tile class="2">: This line represents the initial game tile with a value of 2.
```
 <!-- Game Board Container -->
    <div id="board">
        <!-- Tile Container -->
        <div class="icon">
            <!-- Game Tile (initially with a value of 2) -->
            <tile class="2"></tile>
        </div>
        <!-- More tiles would be added dynamically within this container during gameplay using js -->
    </div>
    ```
