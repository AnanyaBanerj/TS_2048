
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

Add the CSS link and the JS link that will be used in the project in the head tag. 

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

- div id="board": This is the main container for the game board. It represents the grid where the game tiles will be placed and moved.

- div class="icon": Inside the game board container, there is a nested div element with the class "icon." This is used to style or position the game tiles within the grid.

- tile class="2": This line represents the initial game tile with a value of 2.
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

## CSS

- Make a CSS file and name it style.css.


Make the text inside the body element of the specified font stack (Arial, Helvetica, or a generic sans-serif font) and center-align the text within the body.

```
body {
    font-family: Arial, Helvetica, sans-serif;
    text-align: center;
}
```

Set the width of the horizontal rule (hr) to 500px.

```
hr {
    width: 500px;
}
```
Now we create the styling for the board element.
- Sets the width and height of the "board" element to 400 pixels by 400 pixels, making it a square.

- Sets the background color of the "board" element to a light grayish-brown color with the hexadecimal code #cdc1b5.

- Adds a border to the "board" element. It's a solid border with a width of 9 pixels and a color of #bbada0, which is a slightly darker shade of grayish-brown.

- Using the "margin: 0 auto", **CENTERS** the div its container by setting the left and right margins to auto.

- flex-wrap: wrap;: Make the display a flexbox by making the display, flex. Use flex wrap, to wrap onto multiple lines if they exceed the available space horizontally.

```
#board {
    width: 400px;
    height: 400px;

    background-color: #cdc1b5;
    border: 9px solid #bbada0;

    margin: 0 auto;
    display: flex;
    flex-wrap: wrap;
}
```

The next block of code describes the styling for the tiles inside the board.

- Sets the width and height of "tile" elements to 90 pixels, creating a square shape.

- Add a solid border of width 5 pixels and the color - #bbada0.

- Sets the font size to 40 pixels and makes the text inside the "tile" elements bold using font-weight.

- the last 3 lines of code center the child elements both horizontally and vertically within a flex container.

```
.tile {
    width: 90px;
    height: 90px;
    border: 5px solid #bbada0;

    font-size: 40px;
    font-weight: bold;
    display: flex;
    justify-content: center;
    align-items: center;
}
```

The next set of codes specifies a background color and text color for every tile with a specific value. The colors can be modified according to personal preference but given are the standard ones. 

```
.x2 {
    background-color: #eee4da;
    color: #727371;
}

.x4 {
    background-color: #ece0ca;
    color: #727371;
}

.x8 {
    background-color: #f4b17a;
    color: white;
}

.x16{
    background-color: #f59575;
    color: white;
}

.x32{
    background-color: #f57c5f;
    color: white;
}

.x64{
    background-color: #f65d3b;
    color: white;
}

.x128{
    background-color: #edce71;
    color: white;
}

.x256{
    background-color: #edcc63;
    color: white;
}

.x512{
    background-color: #edc651;
    color: white;
}

.x1024{
    background-color: #eec744;
    color: white;
}

.x2048{
    background-color: #ecc230;
    color: white;
}

.x4096 {
    background-color: #fe3d3d;
    color: white;
}

.x8192 {
    background-color: #ff2020;
    color: white;
}
```
## JS 

Create a file 2048.js, this will allow you to create a dynamic and interactive web page to execute complex actions.

#### Variable Declarations:


```
var board;
var score = 0;
var rows = 4;
var columns = 4;
```


**Window.onload** sets up an event handler that triggers the setGame() function when the web page has fully loaded. The setGame() function will be elaborated later. 
```
window.onload = function() {
    setGame();
}
```
#### setGame() Function:

This function initializes the game by:
- Creats an empty game board represented as a 4x4 grid with all values initially set to 0.
- Creating HTML div elements to visually represent each tile on the game board.
- Adding the tiles to the HTML document within an element with the ID "board."
Calling setTwo() twice to add two "2" tiles to random empty positions on the board.
```
function setGame() {
   

    board = [
        [0, 0, 0, 0],
        [0, 0, 0, 0],
        [0, 0, 0, 0],
        [0, 0, 0, 0]
    ]

    for (let r = 0; r < rows; r++) {
        for (let c = 0; c < columns; c++) {
            let tile = document.createElement("div");
            tile.id = r.toString() + "-" + c.toString();
            let num = board[r][c];
            updateTile(tile, num);
            document.getElementById("board").append(tile);
        }
    }
  
    setTwo();
    setTwo();

}
```

**updateTile Function:**
The `updateTile` function is responsible for updating the appearance of a game tile based on its numeric value. Here's a breakdown of what this function does:

- `tile.innerText = "";`: Clears the text content of the tile, ensuring that it's initially empty.

- Clear all the CSS classes applied to the tile using `tile.classList.value = ""; `. Then add the class tile to the tile element. 

- `tile.classList.add("tile");`: Adds the class "tile" to the tile element. This class typically defines the default styling for game tiles.

- `if (num > 0) { ... }`: This conditional block checks if the provided `num` (the numeric value of the tile) is greater than 0. `tile.innerText = num.toString();` is used to update the string representation to `num`

- `if (num <= 4096) { ... }`: This conditional block checks if `num` is less than or equal to 4096.

   - If `num` is less than or equal to 4096, it adds a class in the format "x[num]" to the tile. Else it adds the class x8192 to the tile, which is the highest possible value. 

```
function updateTile(tile, num) {
    tile.innerText = "";
    tile.classList.value = ""; 
    tile.classList.add("tile");
    if (num > 0) {
        tile.innerText = num.toString();
        if (num <= 4096) {
            tile.classList.add("x"+num.toString());
        } else {
            tile.classList.add("x8192");
        }                
    }
}
```
**Keyboard Event Listener**
Add an event listener to the document for the "keyup" event, which fires when a keyboard key is released. 
Inside the event listener, it checks which arrow key was released using e.code:
- `if (e.code == "ArrowLeft") { ... }:` Release the left arrow key, it calls the slideLeft() function to slide the tiles to the left and merges them , and then calls setTwo() to add a new "2" tile to the board.
The same thing is done for Arrowright, Arrowup and ArrowDown. 
- After handling the tile movement based on the arrow key press, it updates the score displayed on the web page using `document.getElementById("score").innerText = score;`
```
document.addEventListener('keyup', (e) => {
    if (e.code == "ArrowLeft") {
        slideLeft();
        setTwo();
    }
    else if (e.code == "ArrowRight") {
        slideRight();
        setTwo();
    }
    else if (e.code == "ArrowUp") {
        slideUp();
        setTwo();

    }
    else if (e.code == "ArrowDown") {
        slideDown();
        setTwo();
    }
    document.getElementById("score").innerText = score;
})
```

