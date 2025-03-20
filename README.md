# help-yourself
stuff to help you
exemplar
drawsql draw data chart

gdpr standards
acceptance standards
ethics

cloud
need for security

functional
service the user requires
non functional
constaints under which  it operates and is developed 

https://www.w3.org/WAI/cognitive/#about-accessibility-for-people-with-cognitive-and-learning-disabilities

refrence it for more points, good practice, not law, but highly recommended
admin view client view, do a little bit about it though definitally talk about it if you dont have enough time





setting a timeout to revert the text back to its original state after a few seconds. example:

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Change Text Example</title>
</head>
<body>
    <p id="message">Original Text</p>
    <button onclick="confirmChange()">Confirm Change</button>

    <script>
        function confirmChange() {
            const messageElement = document.getElementById('message');
            messageElement.textContent = 'Text has been changed!';
            
            // Revert text back to original after 3 seconds
            setTimeout(() => {
                messageElement.textContent = 'Original Text';
            }, 3000);
        }
    </script>
</body>
</html>

To perform mathematical operations within an HTML, use JavaScript. JavaScript can be used to manipulate and calculate values. example:

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mathematical Operations Example</title>
</head>
<body>
    <h1>Simple Calculator</h1>
    <input type="number" id="num1" placeholder="Enter first number">
    <input type="number" id="num2" placeholder="Enter second number">
    <button onclick="calculate()">Calculate</button>
    <p id="result"></p>

    <script>
        function calculate() {
            const num1 = parseFloat(document.getElementById('num1').value);
            const num2 = parseFloat(document.getElementById('num2').value);
            const sum = num1 + num2;
            const difference = num1 - num2;
            const product = num1 * num2;
            const quotient = num1 / num2;

            document.getElementById('result').innerHTML = `
                Sum: ${sum}<br>
                Difference: ${difference}<br>
                Product: ${product}<br>
                Quotient: ${quotient}
            `;
        }
    </script>
</body>
</html>

use JavaScript to highlight or show information about an element that the mouse is hovering over. Here's an example that changes the background color of the element when the mouse hovers over it:

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hover Highlight Example</title>
    <style>
        .hoverable {
            padding: 10px;
            margin: 5px;
            border: 1px solid #ccc;
        }
        .hoverable:hover {
            background-color: yellow;
        }
    </style>
</head>
<body>
    <div class="hoverable">Item 1</div>
    <div class="hoverable">Item 2</div>
    <div class="hoverable">Item 3</div>
    <div class="hoverable">Item 4</div>

    <script>
        const hoverableElements = document.querySelectorAll('.hoverable');

        hoverableElements.forEach(element => {
            element.addEventListener('mouseover', () => {
                element.style.backgroundColor = 'yellow';
            });

            element.addEventListener('mouseout', () => {
                element.style.backgroundColor = '';
            });
        });
    </script>
</body>
</html>
In this example:

The CSS .hoverable:hover selector changes the background color to yellow when the mouse hovers over an element with the class hoverable.
The JavaScript adds mouseover and mouseout event listeners to each hoverable element to change the background color when the mouse enters and leaves the element.

connect and grab tables to display them

<?php
//dATABASE CONNECTIO PARAMETERS
$servername = "localhost";
$username = "root";
$password = "";
$dbname = "bean 2";

//$conn = new mysqli($host, $user, $password, $database);

/*if ($conn->connect_error) 
{

    die("Connection failed: " . $conn->connect_error);
    
 }*/

 try {
    $conn= new PDO("mysql:host=$servername;dbname=$dbname", $username, $password);
    $conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
} catch (PDOException $e){
    echo "Connection failed: " . $e->getMessage();
} 

 $sql = "SELECT * FROM menu";

 // Fetch Menu for Dropdown
 //$stmt = $conn->prepare($sql);
$menu_result = $conn->query($sql);

$menu_options = "";

while ($row = $menu_result->fetch(PDO::FETCH_ASSOC)) {

$menu_options .= "<option value='" . $row['id'] . "'>" . $row['item_name'] . " - $" . $row['price'] . "</option>";

}


// Fetch Available Tables and Times

$tables_result = $conn->query("SELECT * FROM tables");

$tables = [];

while ($row = $tables_result->fetch(PDO::FETCH_ASSOC)) {

$tables[] = $row;

}


//$conn->close();
$conn = null;

?>


<!DOCTYPE html>

<html>

<head>
