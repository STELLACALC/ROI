<!DOCTYPE html>
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
            background: linear-gradient(to bottom, #f4f4f9, #e0e0e5);
            color: #333;
        }
        .container {
            max-width: 450px;
            margin: auto;
            background: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
            border-top: 6px solid #0077ff;
        }
        .header {
            text-align: center;
            margin-bottom: 20px;
        }
        .header h1 {
            font-size: 26px;
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
            width: 90%;
            padding: 12px;
            margin: 0 auto 15px auto;
            display: block;
            border: 1px solid #ccc;
            border-radius: 5px;
            font-size: 16px;
            text-align: center;
        }
        button {
            width: 100%;
            padding: 12px;
            background-color: #0077ff;
            color: white;
            border: none;
            border-radius: 5px;
            font-size: 18px;
            cursor: pointer;
            transition: 0.3s ease;
        }
        button:hover {
            background-color: #005bb5;
        }
        .result {
            margin-top: 20px;
            padding: 15px;
            background-color: #f1f1f1;
            border-radius: 5px;
            font-size: 20px;
            text-align: center;
            color: #333;
            font-weight: bold;
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
        .reset-btn {
            width: 100%;
            padding: 10px;
            background-color: #ff4444;
            color: white;
            border: none;
            border-radius: 5px;
            font-size: 16px;
            cursor: pointer;
            margin-top: 10px;
            transition: 0.3s ease;
        }
        .reset-btn:hover {
            background-color: #cc0000;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>STELLA ROI Calculator</h1>
        </div>
        <label for="repairOrder">Average Repair Order ($):</label>
        <input type="number" id="repairOrder" placeholder="Enter average RO value" oninput="calculateROI()">

        <label for="showRate">Appointment Show Rate (%):</label>
        <input type="number" id="showRate" placeholder="Enter show rate percentage" oninput="calculateROI()">

        <label for="bookedAppointments">Booked Appointments:</label>
        <input type="number" id="bookedAppointments" placeholder="Enter number of appointments" oninput="calculateROI()">

        <button onclick="calculateROI()">Calculate ROI</button>
        <button class="reset-btn" onclick="resetFields()">Reset</button>

        <div id="result" class="result" style="display: none;"></div>

        <div class="branding">
            <p>Powered by STELLA Automotive AI</p>
        </div>
    </div>

    <script>
        function calculateROI() {
            const repairOrder = parseFloat(document.getElementById('repairOrder').value);
            const showRate = parseFloat(document.getElementById('showRate').value);
            const bookedAppointments = parseInt(document.getElementById('bookedAppointments').value);

            if (isNaN(repairOrder) || isNaN(showRate) || isNaN(bookedAppointments) || repairOrder <= 0 || showRate <= 0 || bookedAppointments <= 0) {
                document.getElementById('result').style.display = 'none';
                return;
            }

            const showRateDecimal = showRate / 100;
            const roi = repairOrder * showRateDecimal * bookedAppointments;
            
            document.getElementById('result').style.display = 'block';
            document.getElementById('result').textContent = `Estimated ROI: $${roi.toLocaleString(undefined, { minimumFractionDigits: 2, maximumFractionDigits: 2 })}`;
        }

        function resetFields() {
            document.getElementById('repairOrder').value = '';
            document.getElementById('showRate').value = '';
            document.getElementById('bookedAppointments').value = '';
            document.getElementById('result').style.display = 'none';
        }
    </script>
</body>
</html>
