<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>STELLA ROI Calculator</title>
    <style>
        @font-face {
            font-family: 'Caviar Dreams';
            src: url('https://fonts.cdnfonts.com/s/16508/CaviarDreams.woff') format('woff');
        }
        body {
            font-family: 'Caviar Dreams', Arial, sans-serif;
            margin: 20px;
            padding: 0;
            background-color: #f4f4f9;
            color: #333;
        }
        .container {
            max-width: 450px;
            margin: auto;
            background: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            border-top: 6px solid #0077ff;
        }
        .header {
            text-align: center;
            margin-bottom: 20px;
        }
        .header h1 {
            font-size: 24px;
            color: #0077ff;
            margin: 0;
        }
        label {
            display: block;
            margin: 10px 0 5px;
            font-weight: bold;
            text-align: center;
        }
        input[type="number"] {
            width: 80%;
            padding: 10px;
            margin: 0 auto 15px auto;
            display: block;
            border: 1px solid #ddd;
            border-radius: 5px;
        }
        button {
            width: 100%;
            padding: 10px;
            background-color: #0077ff;
            color: white;
            border: none;
            border-radius: 5px;
            font-size: 16px;
            cursor: pointer;
        }
        button:hover {
            background-color: #005bb5;
        }
        .result {
            margin-top: 20px;
            padding: 15px;
            background-color: #f1f1f1;
            border-radius: 5px;
            font-size: 18px;
            text-align: center;
            color: #333;
        }
        .branding {
            text-align: center;
            margin-top: 20px;
        }
        .branding p {
            margin-top: 10px;
            font-size: 14px;
            color: #666;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>STELLA ROI Calculator</h1>
        </div>
        <label for="repairOrder">Average Repair Order ($):</label>
        <input type="number" id="repairOrder" placeholder="Enter average RO value">

        <label for="showRate">Appointment Show Rate (%):</label>
        <input type="number" id="showRate" placeholder="Enter show rate percentage">

        <label for="bookedAppointments">Booked Appointments:</label>
        <input type="number" id="bookedAppointments" placeholder="Enter number of appointments">

        <button onclick="calculateROI()">Calculate ROI</button>

        <div id="result" class="result" style="display: none;"></div>

        <div class="branding">
            <p>Powered by STELLA Automotive AI</p>
        </div>
    </div>

    <script>
        function calculateROI() {
            // Get input values
            const repairOrder = parseFloat(document.getElementById('repairOrder').value);
            const showRate = parseFloat(document.getElementById('showRate').value);
            const bookedAppointments = parseInt(document.getElementById('bookedAppointments').value);

            // Validate inputs
            if (isNaN(repairOrder) || isNaN(showRate) || isNaN(bookedAppointments)) {
                alert('Please enter valid numbers for all fields.');
                return;
            }

            // Calculate ROI
            const showRateDecimal = showRate / 100; // Convert percentage to decimal
            const roi = repairOrder * showRateDecimal * bookedAppointments;

            // Display result
            const resultDiv = document.getElementById('result');
            resultDiv.style.display = 'block';
            resultDiv.textContent = `Estimated ROI: $${roi.toFixed(2)}`;
        }
    </script>
</body>
</html>
