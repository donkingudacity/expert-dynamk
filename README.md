<html>
<head>
    <title>Pixel Art Maker!</title>
    <link rel="stylesheet" href="https://fonts.googleapis.com/css?family=Monoton">
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <h1>Lab: Pixel Art Maker</h1>

    <h2>Choose Grid Size</h2>
    <form id="sizePicker">
        Grid Height:
        <input type="number" id="inputHeight" name="height" min="1" value="1">
        Grid Width:
        <input type="number" id="inputWidth" name="width" min="1" value="1">
        <input type="submit">
    </form>

    <h2>Pick A Color</h2>
    <input type="color" id="colorPicker">

    <h2>Design Canvas</h2>
    <table id="pixelCanvas"></table>

    <script src="designs.js"></script>
</body>
</html>
body {
    text-align: center;
}

h1 {
    font-family: Monoton;
    font-size: 70px;
    margin: 0.2em;
}

h2 {
    margin: 1em 0 0.25em;
}

h2:first-of-type {
    margin-top: 0.5em;
}

table,
tr,
td {
    border: 1px solid black;
}

table {
    border-collapse: collapse;
    margin: 0 auto;
}

tr {
    height: 20px;
}

td {
    width: 20px;
}

input[type=number] {
    width: 6em;
}
// Select color input
let colorSelected = $("#colorPicker").val();

// When size is submitted by the user, call makeGrid()
$("#sizePicker").on("submit",function(makeGrid) {
  let pixelCanvas= $("#pixelCanvas");
  let tbody =$("<tbody></tbody>");// this is a cache used to improve performance
  
  let td, tr;//defining the variables used for the grids rows and columns
  
  let height = $("#inputHeight").val();//accepting the height value from the form
  let width = $("#inputWidth").val();//accepting the width value from the form
  pixelCanvas.empty();//clears the old grid before creating the new grid
  
  /*Two loops (One For Loop And a While Loop as per Project Specs) to create the grid based on the inputted height and width*/
 for(let row =0; row < height; row++){
   tr = $("<tr></tr>");
   
   let col = 0; // when to start
while (col < width) { // when to stop
   td = $("<td></td>");
     tr.append(td);
  col++; // how to get to the next item
}
  
   tbody.last().append(tr);
    
 }
  //Add grid to DOM
  pixelCanvas.append(tbody);

  //Event Listener that enables user to Color square when clicked as well as when mouse ios dragged to color multiple cells
    pixelCanvas.on("mousedown mouseover", "td", function(e) {
    
    if (e.buttons === 1) {
    
    //change background color of target square
    $(this).css("background-color", $("#colorPicker").val());
    }
  });
  
makeGrid.preventDefault();
});
