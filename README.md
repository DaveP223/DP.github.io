<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fruit Sales Bar Chart</title>
</head>
<body>
<canvas id="myCanvas" width="400" height="300"></canvas>
<script>
    // Define the data as a JSON array
    var fruitSales = [
        {name: "Apple", quantity: 20, color: "red", quantityX: 17, quantityY: 15},
        {name: "Orange", quantity: 10, color: "orange", quantityX: 17, quantityY: 15},
        {name: "Banana", quantity: 15, color: "yellow", quantityX: 17, quantityY: 15},
        {name: "Kiwi", quantity: 5, color: "green", quantityX: 17, quantityY: 15},
        {name: "Blueberry", quantity: 5, color: "blue", quantityX: 17, quantityY: 15},
        {name: "Grapes", quantity: 10, color: "purple", quantityX: 17, quantityY: 15}
    ];

    // Get the canvas element and its context
    var canvas = document.getElementById('myCanvas');
    var fruits = canvas.getContext('2d');

    // Define bar chart parameters
    var fruitbarHeight = 40;
    var fruitbarSpacing = 0;
    var startX = 50;
    var startY = 20;
   var maxQuantity = 0; // Initialize maxQuantity with a default value

for (var i = 0; i < fruitSales.length; i++) {
    if (fruitSales[i].quantity > maxQuantity) {
        maxQuantity = fruitSales[i].quantity;
    }
}
    var chartWidth = canvas.width - 2 * startX;

    // Draw bars for each fruit
    fruitSales.forEach(function(fruit, index) {
        var fruitbarWidth = (fruit.quantity / maxQuantity) * chartWidth;
        var barX = startX;
        var barY = startY + (fruitbarHeight + fruitbarSpacing) * index;

        // Draw bar
        fruits.fillStyle = fruit.color;
        fruits.fillRect(barX, barY, fruitbarWidth, fruitbarHeight);

        // Draw fruit name
        fruits.fillStyle = 'black';
        fruits.fillText(fruit.name, barX + 10, barY + fruitbarHeight / 2 + 5);

        // Draw quantity at specified coordinates within the bar
        fruits.fillText(fruit.quantity, barX + fruit.quantityX, barY + fruit.quantityY);
    });

</script>
</body>
</html>
