# Youtube-Playback-Speed-Calculator-X

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Time Calculator</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background-color: #f4f4f9;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }

        .container {
            background-color: #ffffff;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            max-width: 350px;
            width: 100%;
            text-align: center;
        }

        h2 {
            color: #333;
            margin-bottom: 20px;
        }

        label {
            display: block;
            margin: 10px 0 5px;
            color: #555;
            font-weight: bold;
        }

        input {
            width: 100%;
            padding: 10px;
            margin-bottom: 15px;
            border: 1px solid #ccc;
            border-radius: 5px;
            font-size: 16px;
        }

        button {
            background-color: #007bff;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 5px;
            font-size: 16px;
            cursor: pointer;
            transition: background-color 0.3s ease;
        }

        button:hover {
            background-color: #0056b3;
        }

        .result {
            margin-top: 20px;
            font-size: 1.2em;
            color: #333;
        }

        .result span {
            font-weight: bold;
            color: #007bff;
        }

        .footer {
            margin-top: 20px;
            font-size: 0.9em;
            color: #777;
        }
    </style>
</head>
<body>
    <div class="container">
        <h2>Time Calculator</h2>
        <label for="hours">Hours:</label>
        <input type="number" id="hours" min="0" value="0">

        <label for="minutes">Minutes:</label>
        <input type="number" id="minutes" min="0" max="59" value="0">

        <label for="seconds">Seconds:</label>
        <input type="number" id="seconds" min="0" max="59" value="0">

        <label for="speed">Playback Speed:</label>
        <input type="number" id="speed" min="0.1" step="0.1" value="1.0">

        <button onclick="calculateTime()">Calculate</button>

        <div class="result">
            <p>Calculated Time: <span id="calculatedTime">00:00:00</span></p>
            <p>Time Saved: <span id="timeSaved">00:00:00</span></p>
        </div>

        <div class="footer">
            Made By Bhovwtik
        </div>
    </div>

    <script>
        function calculateTime() {
            const hours = parseInt(document.getElementById('hours').value) || 0;
            const minutes = parseInt(document.getElementById('minutes').value) || 0;
            const seconds = parseInt(document.getElementById('seconds').value) || 0;
            const speed = parseFloat(document.getElementById('speed').value) || 1;

            if (speed <= 0) {
                alert("Speed must be greater than 0");
                return;
            }

            const totalSeconds = hours * 3600 + minutes * 60 + seconds;
            const calculatedSeconds = totalSeconds / speed;
            const savedSeconds = totalSeconds - calculatedSeconds;

            document.getElementById('calculatedTime').textContent = formatTime(calculatedSeconds);
            document.getElementById('timeSaved').textContent = formatTime(savedSeconds);
        }

        function formatTime(totalSeconds) {
            const hours = Math.floor(totalSeconds / 3600);
            const minutes = Math.floor((totalSeconds % 3600) / 60);
            const seconds = Math.floor(totalSeconds % 60);

            return `${pad(hours)}:${pad(minutes)}:${pad(seconds)}`;
        }

        function pad(num) {
            return num < 10 ? `0${num}` : num;
        }
    </script>
</body>
</html>
