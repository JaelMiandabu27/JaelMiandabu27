<html>
    <head>
        <title>Calculator</title>
    </head>
    <style>
        table{
            border: 2px solid black;
            margin-left:auto;
            margin-right:auto;
            border-radius:5px;
            
        }
        input[type="button"]{
            width: 100%;
            padding: 30px  50px;
            background-color: green;
            color: white;
            font-size:24px;
            font-weight: bold;
            border: none;
            border-radius: 5px;
        }
        input[type="text"]{
            border:none;
            outline: none; /*Removed the outline when focused*/
            padding: 25px 40px;
            border-radius: 5px;
            font-size: 24px;
            font-weight:bold;

        }
    </style>
<body>
  <table id="calcu">
    <tr>
        <td colspan="3"><input type="text" id="result"></td>
        <td><input type="button" value="c" onclick="clr()"></td>
    </tr>
    <tr>
       <td><input type="button" value="1" onclick="dis('1')" onkeydown="myFunction(event)"></td> 
       <td><input type="button" value="2" onclick="dis('2')" onkeydown="myFunction(event)"> </td> 
       <td><input type="button" value="3" onclick="dis('3')" onkeydown="myFunction(event)"></td> 
       <td><input type="button" value="/" onclick="dis('/')" onkeydown="myFunction(event)"></td> 
    </tr>

    <tr>
        <td><input type="button" value="4" onclick="dis('4')" onkeydown="myFunction(event)"></td> 
        <td><input type="button" value="5" onclick="dis('5')" onkeydown="myFunction(event)"> </td> 
        <td><input type="button" value="6" onclick="dis('6')" onkeydown="myFunction(event)"></td> 
        <td><input type="button" value="*" onclick="dis('*')" onkeydown="myFunction(event)"></td>  
    </tr>

    <tr>
        <td><input type="button" value="7" onclick="dis('7')" onkeydown="myFunction(event)"></td> 
       <td><input type="button" value="8" onclick="dis('8')" onkeydown="myFunction(event)"> </td> 
       <td><input type="button" value="9" onclick="dis('9')" onkeydown="myFunction(event)"></td> 
       <td><input type="button" value="-" onclick="dis('-')" onkeydown="myFunction(event)"></td> 
    </tr>

    <tr>
        <td><input type="button" value="0" onclick="dis('0')" onkeydown="myFunction(event)"></td> 
       <td><input type="button" value="." onclick="dis('.')" onkeydown="myFunction(event)"> </td> 
       <td><input type="button" value="=" onclick="solve()" onkeydown="myFunction(event)"></td> 
       <td><input type="button" value="+" onclick="dis('+')" onkeydown="myFunction(event)"></td> 
    </tr>
    </tr>
  </table>  
  <script>
    
    // Function to display the value in the input field
function dis(val) {
    document.getElementById("result").value += val;
}

// Function to clear the input field
function clr() {
    document.getElementById("result").value = '';
}

// Function to evaluate the expression in the input field
function solve() {
    try {
        let x = document.getElementById("result").value;
        let y = eval(x); // Evaluates the string as a mathematical expression
        document.getElementById("result").value = y;
    } catch (error) {
        alert("Invalid Expression");
        clr();
    }
}

// Event listener for keyboard input
document.addEventListener('keydown', function (event) {
    const allowedKeys = ['0', '1', '2', '3', '4', '5', '6', '7', '8', '9', '+', '-', '*', '/' ,'.'];
    const resultField = document.getElementById("result");

    if (allowedKeys.includes(event.key)) {
        dis(event.key); // Add the key to the display
    } else if (event.key === 'Enter') {
        solve(); // Calculate the result
    } else if (event.key === 'Backspace') {
        resultField.value = resultField.value.slice(0, -1); // Remove the last character
    }
});
 
  </script>
</body>

</html>
