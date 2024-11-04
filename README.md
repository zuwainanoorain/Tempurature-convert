# Tempurature-convert
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Temperature Converter</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <div class="container">
    <h1>Temperature Converter</h1>
    
    <form action="convert.php" method="POST">
      <div class="input-group">
        <label for="temperature">Degrees</label>
        <input type="number" name="temperature" id="temperature" placeholder="72" required>
        <select name="fromUnit" id="fromUnit">
          <option value="fahrenheit" selected>Fahrenheit</option>
          <option value="celsius">Celsius</option>
          <option value="kelvin">Kelvin</option>
        </select>
      </div>

      <button type="submit">Convert</button>
    </form>

    <div class="result-group">
      <label for="result">Result</label>
      <p id="result">
        <?php
          // Include your PHP conversion logic here
          if ($_SERVER["REQUEST_METHOD"] == "POST") {
            $temperature = $_POST['temperature'];
            $fromUnit = $_POST['fromUnit'];
            $result = '';

            // Convert based on the selected unit
            if ($fromUnit == "fahrenheit") {
              $result = ($temperature - 32) * 5 / 9; // Fahrenheit to Celsius
              echo number_format($result, 4) . " °C";
            } elseif ($fromUnit == "celsius") {
              $result = ($temperature * 9 / 5) + 32; // Celsius to Fahrenheit
              echo number_format($result, 4) . " °F";
            } elseif ($fromUnit == "kelvin") {
              $result = $temperature - 273.15; // Kelvin to Celsius
              echo number_format($result, 4) . " °C";
            }
          }
        ?>
      </p>
    </div>
  </div>
</body>
</html>
.container {
  text-align: center;
  margin: 20px;
  background-color: #f9f9f9; 
  padding: 20px;
  border-radius: 10px; 
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1); 
}

.input-group {
  margin-bottom: 20px; 
}

label {
  display: block; 
  font-size: 18px; 
  margin-bottom: 5px; 
}

input, select {
  padding: 10px;
  font-size: 16px;
  width: calc(50% - 22px); 
  margin-right: 10px; 
}

input {
  border: 1px solid #ccc; 
  border-radius: 5px; 
}

select {
  border: 1px solid #ccc; 
  border-radius: 5px; 
}

.result-group {
  margin-top: 20px; 
}

#result {
  font-size: 24px; 
  font-weight: bold;
  margin-top: 5px; 
}

button {
  padding: 10px 20px;
  font-size: 16px;
  background-color: #007bff; 
  color: white; 
  border: none; 
  border-radius: 5px;
  cursor: pointer; 
}

button:hover {
  background-color: #0056b3; 
}
