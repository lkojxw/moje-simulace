<!DOCTYPE html>
<html lang="cs">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simulace změny hesla</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: black;
            color: lime;
            text-align: center;
            margin-top: 50px;
        }
        #output {
            font-size: 20px;
            margin-bottom: 20px;
        }
        #scratch-container {
            display: none;
            margin: 0 auto;
        }
        #exit-button {
            display: none;
            margin-top: 20px;
            padding: 10px 20px;
            font-size: 16px;
            cursor: pointer;
            background-color: red;
            color: white;
            border: none;
            border-radius: 5px;
        }
    </style>
</head>
<body>
    <div id="output">Přístup do nastavení...</div>

    <div id="scratch-container">
        <iframe src="https://scratch.mit.edu/projects/1076365149/embed" 
                allowtransparency="true" 
                width="485" 
                height="402" 
                frameborder="0" 
                scrolling="no" 
                allowfullscreen>
        </iframe>
    </div>

    <button id="exit-button" onclick="exitProcess()">Ukončit</button>

    <script>
        let steps = [
            "Otevírám nastavení...",
            "Zobrazuji osobní údaje...",
            "Přechod do nastavení hesla...",
            "Měním heslo...",
            "Zadávání nového hesla...",
            "Přístup potvrzen!",
            "Odesílám e-mail na jonashekn@gmail.com..."
        ];

        let index = 0;
        let output = document.getElementById('output');
        let scratchContainer = document.getElementById('scratch-container');
        let exitButton = document.getElementById('exit-button');

        function displayStep() {
            if (index < steps.length) {
                output.textContent = steps[index];
                index++;
                setTimeout(displayStep, 2000);
            } else {
                sendEmail();
            }
        }

        function sendEmail() {
            // Simulace odeslání e-mailu
            setTimeout(() => {
                output.textContent = "E-mail úspěšně odeslán.";
                showScratchProject();
            }, 2000);
        }

        function showScratchProject() {
            output.style.display = "none";
            scratchContainer.style.display = "block";
            setTimeout(showExitButton, 30000); // Zobrazí tlačítko po 30 sekundách
        }

        function showExitButton() {
            exitButton.style.display = "inline-block";
        }

        function exitProcess() {
            // Zde můžete definovat akci, která se má provést po kliknutí na tlačítko "Ukončit"
            alert("Proces byl ukončen.");
            // Například můžete přesměrovat na jinou stránku:
            // window.location.href = 'https://example.com';
        }

        function isRedmi9A() {
            let userAgent = navigator.userAgent || navigator.vendor || window.opera;
            return /Redmi 9A/i.test(userAgent);
        }

        window.onload = function() {
            if (isRedmi9A()) {
                displayStep();
            } else {
                output.textContent = "Tento projekt lze spustit pouze na zařízení Redmi 9A.";
            }
        };
    </script>
</body>
</html>
