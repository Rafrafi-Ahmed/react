<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Timer</title>
</head>
<style>
    .block {
        background-color: aqua;
        text-align: center;
        padding: 20px;
    }

    .counter {
        display: flex;
        justify-content: center;
        gap: 10px;
        font-size: 24px;
    }

    .buttons {
        display: flex;
        justify-content: center;
        gap: 10px;
    }
</style>
<body>
    <div class="block">
        <div class="counter">
            <div class="hours">00</div>
            <div class="twoPoints">:</div>
            <div class="minutes">00</div>
            <div class="twoPoints">:</div>
            <div class="seconds">00</div>
        </div>
        <div class="buttons">
            <button id="Démarrer" type="button">Démarrer</button>
            <button id="pause" type="button">Pause</button>
            <button id="Réinitialiser" type="button">Réinitialiser</button>
        </div>
    </div>

    <script>
        const secondsDisplay = document.querySelector('.seconds');
        const minutesDisplay = document.querySelector('.minutes');
        const hoursDisplay = document.querySelector('.hours');
        const DémarrerButton = document.getElementById('Démarrer');
        const pauseButton = document.getElementById('pause');
        const RéinitialiserButton = document.getElementById('Réinitialiser');

        let initialSec = 0;
        let initialMin = 0;
        let initialHrs = 0;
        let interval;

        function updateTimer() {
            initialSec++;

            if (initialSec === 60) {
                initialSec = 0;
                initialMin++;

                if (initialMin === 60) {
                    initialMin = 0;
                    initialHrs++;
                }
            }

            secondsDisplay.textContent = `${initialSec < 10 ? '0' : ''}${initialSec}`;
            minutesDisplay.textContent = `${initialMin < 10 ? '0' : ''}${initialMin}`;
            hoursDisplay.textContent = `${initialHrs < 10 ? '0' : ''}${initialHrs}`;
        }

        DémarrerButton.addEventListener('click', () => {
            if (!interval) {
                interval = setInterval(updateTimer, 1000);
            }
        });

        pauseButton.addEventListener('click', () => {
            clearInterval(interval);
            interval = null;
        });

        RéinitialiserButton.addEventListener('click', () => {
            clearInterval(interval);
            interval = null;
            initialSec = 0;
            initialMin = 0;
            initialHrs = 0;
            secondsDisplay.textContent = '00';
            minutesDisplay.textContent = '00';
            hoursDisplay.textContent = '00';
        });
    </script>
</body>
</html>
<style>
    body {
        background-color: #000;
        color: #00ff00;
        font-family: "Arial", sans-serif;
        text-align: center;
        margin: 0;
        padding: 0;
    }

    .block {
        background-color: #000;
        text-align: center;
        padding: 20px;
    }

    .counter {
        display: flex;
        justify-content: center;
        gap: 10px;
        font-size: 48px;
        font-weight: bold;
    }

    .counter > div {
        background-color: #000;
        border: 2px solid #00ff00;
        padding: 10px;
        border-radius: 5px;
    }

    .buttons {
        display: flex;
        justify-content: center;
        gap: 10px;
    }

    button {
        background-color: #00ff00;
        color: #000;
        border: none;
        padding: 10px 20px;
        font-size: 18px;
        cursor: pointer;
        border-radius: 5px;
        transition: background-color 0.3s ease;
    }

    button:hover {
        background-color: #009900;
    }
</style>
