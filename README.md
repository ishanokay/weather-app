# using-ai
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Weather App</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            background: linear-gradient(to right, #36D1DC, #5B86E5);
            color: white;
        }
        .container {
            background: rgba(255, 255, 255, 0.2);
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
            text-align: center;
        }
        input {
            padding: 10px;
            margin-right: 10px;
            border: none;
            border-radius: 5px;
        }
        button {
            padding: 10px;
            background: #ff9800;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        .result {
            margin-top: 20px;
            font-size: 20px;
        }
        .footer {
            margin-top: 20px;
            font-size: 14px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Weather App</h1>
        <p>Made with ❤️ by Ishan Bansal</p>
        <input type="text" id="city" placeholder="Enter city">
        <button onclick="getWeather()">Get Weather</button>
        <p class="result" id="result"></p>
    </div>
    

    <script>
        async function getWeather() {
            const city = document.getElementById("city").value;
            if (!city) {
                alert("Please enter a city");
                return;
            }
            const apiKey = "78531af525104956912172254251102";
            const url = `http://api.weatherapi.com/v1/current.json?key=${apiKey}&q=${city}&aqi=yes`;
            try {
                const response = await fetch(url);
                const data = await response.json();
                if (data.error) {
                    document.getElementById("result").textContent = "City not found";
                } else {
                    document.getElementById("result").textContent = `Temperature: ${data.current.temp_c}°C`;
                }
            } catch (error) {
                document.getElementById("result").textContent = "Failed to fetch weather";
            }
        }
    </script>
</body>
</html>
