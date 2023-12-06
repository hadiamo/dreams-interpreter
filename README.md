<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Dream Interpreter</title>
</head>
<body>
  <label for="dreamInput">Enter your dream:</label>
  <input type="text" id="dreamInput">
  <button id="interpretButton">Interpret Dream</button>
  <div id="interpretationResult"></div>
  <script src="your-script.js"></script>
</body>
</html>
<!DOCTYPE html>
<html>
<head>
    <title>Dream Interpreter</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background: linear-gradient(to bottom right, #4E3A4C, #2E2945);
            color: #fff;
            margin: 0;
        }

        .container {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
        }

        .title {
            font-size: 32px;
            font-weight: bold;
            margin-bottom: 20px;
        }

        .options {
            display: flex;
            justify-content: center;
            gap: 40px;
        }

        .option {
            display: flex;
            justify-content: center;
            align-items: center;
            width: 200px;
            height: 200px;
            border-radius: 50%;
            font-size: 16px;
            font-weight: bold;
            cursor: pointer;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }

        .option:hover {
            transform: scale(1.1);
            box-shadow: 0 0 10px rgba(255, 255, 255, 0.3);
        }

        .nightmares {
            background-color: #880cad;
        }

        .recurring-dreams {
            background-color: #580963;
        }

        .lucid-dreams {
            background-color: #771e80;
        }

        .dream-input-container {
            display: none;
            margin-top: 40px;
        }

        .input-container {
            margin-bottom: 10px;
        }

        .interpretation-container {
            text-align: center;
        }

        .interpretation-box {
            width: 300px;
            height: 200px;
            background-color: #ffffff;
            color: rgb(0, 0, 0);
            border: none;
            border-radius: 5px;
            padding: 10px;
            margin-top: 20px;
            resize: none;
        }

        .back-button {
            margin-top: 20px;
            background-color: #563D4F;
            color: #fff;
            border: none;
            border-radius: 5px;
            padding: 10px 20px;
            cursor: pointer;
            transition: background-color 0.3s ease;
        }

        .back-button:hover {
            background-color: #b77dc9;
        }
       
    </style>
</head>
<body>
    <div class="container">
        <h1 class="title">Dream Interpreter</h1>
        <div class="options">
            <div class="option nightmares" onclick="selectDreamOption('nightmares')">Nightmares</div>
            <div class="option recurring-dreams" onclick="selectDreamOption('recurring-dreams')">Recurring Dreams</div>
            <div class="option lucid-dreams" onclick="selectDreamOption('lucid-dreams')">Lucid Dreams</div>
        </div>
        <div class="dream-input-container">
            <div class="input-container">
                <textarea class="input-box" id="dream" placeholder="Please enter your dream" style="width: 300px; height: 100px; border-radius: 5px; border: none; padding: 10px; margin-bottom: 20px;"></textarea>
            </div>
            <button onclick="interpretDream()" style="background-color: #7D5A80; color: #fff; border: none; border-radius: 5px; padding: 10px 20px; cursor: pointer; transition: background-color 0.3s ease;">Interpret Dream</button>
            <div class="interpretation-container">
                <textarea class="interpretation-box" id="interpretation" readonly placeholder="Interpretation"></textarea>
            </div>
            <button class="back-button" onclick="goBack()">Back</button>
        </div>
      
    </div>

    <script>
        function selectDreamOption(option) {
            var optionsContainer = document.querySelector('.options');
            var dreamInputContainer = document.querySelector('.dream-input-container');
            var selectedOption = document.querySelector('.selected-option');

            if (selectedOption) {
                selectedOption.classList.remove('selected-option');
            }

            optionsContainer.style.display = 'none';
            dreamInputContainer.style.display = 'block';

            var selectedOptionElement = document.querySelector(`.option.${option}`);
            selectedOptionElement.classList.add('selected-option');
        }

        function interpretDream() {
            var dreamInput = document.getElementById('dream').value;
            var interpretationBox = document.getElementById('interpretation');
            
            // Perform interpretation logic based on the dream input
            var interpretation = getDreamInterpretation(dreamInput);
            interpretationBox.value = interpretation;
        }

       function interpretDream() {
         var dreamInput = document.getElementById('dream').value;
         var interpretationBox = document.getElementById('interpretation');
         // Send an AJAX request to the backend server
         var xhr = new XMLHttpRequest();
         xhr.open('POST', '/interpret-dream', true);
         xhr.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded');
         xhr.onreadystatechange = function() {
           if (xhr.readyState === XMLHttpRequest.DONE && xhr.status === 200) {
             var response = JSON.parse(xhr.responseText);
             var interpretation = response.interpretation;
             interpretationBox.value = interpretation;
           }
         };
         xhr.send('dream=' + encodeURIComponent(dreamInput));
       }
       
       function interpretDream() {
    var dreamInput = document.getElementById('dream').value;
    var interpretationBox = document.getElementById('interpretation');
    var selectedOption = document.querySelector('.selected-option');

    if (selectedOption) {
        var optionType = selectedOption.textContent.toLowerCase();

        // Perform interpretation logic based on the selected dream option
        var interpretation = "";

        // Add water-related interpretation for each dream type
        if (optionType === 'nightmares') {
            interpretation = "Dreaming of water in nightmares may symbolize deep emotional turmoil or fear.";
        } else if (optionType === 'recurring dreams') {
            interpretation = "Recurring dreams with water might indicate a persistent emotional issue you need to address.";
        } else if (optionType === 'lucid dreams') {
            interpretation = "Experiencing lucid dreams with water could suggest a heightened awareness of your emotions.";
        }

        interpretationBox.value = interpretation;
    }
}


        function goBack() {
    var optionsContainer = document.querySelector('.options');
    var dreamInputContainer = document.querySelector('.dream-input-container');
    var selectedOption = document.querySelector('.selected-option');
    var dreamInput = document.getElementById('dream');
    var interpretationBox = document.getElementById('interpretation');

    optionsContainer.style.display = 'flex';
    dreamInputContainer.style.display = 'none';

    if (selectedOption) {
        selectedOption.classList.remove('selected-option');
    }

    // Clear the text in the input and interpretation boxes
    dreamInput.value = '';
    interpretationBox.value = '';
}
    </script>
</body>
</html>
