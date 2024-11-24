# Игра «Угадай число»


<style>

    body {

        font-family: Arial, sans-serif;

        text-align: center;

        margin-top: 50px;

    }

    .container {

        max-width: 600px;

        margin: 0 auto;

    }

    .game-message {

        margin: 20px 0;

    }

    .guess-form {

        margin: 20px 0;

    }

   .guess-form input {

        padding: 10px;

        width: 150px;

        font-size: 18px;

        border: 2px solid #007BFF; /* Цвет границы */

        border-radius: 5px; /* Скругленные углы */

        background-color: #f8f9fa; /* Цвет фона */

        box-shadow: 2px 2px 5px rgba(0, 0, 0, 0.1); /* Тень */

        transition: border-color 0.3s; /* Плавный переход цвета границы */

    }

    .guess-form input:focus {

        border-color: #0056b3; /* Цвет границы при фокусировке */

        outline: none; /* Убираем стандартное обрамление */

    }
    .guess-form button {

        padding: 10px 20px;

        background-color: #007BFF;

        color: white;

        border: none;

        border-radius: 5px; /* Скругленные углы кнопки */

        cursor: pointer;

        font-size: 18px;

        transition: background-color 0.3s; /* Плавный переход цвета фона */

    }

    .guess-form button:hover {

        background-color: #0056b3;

    }

</style>


<div class="container">

    <form class="guess-form" id="guessForm">

        <button type="button" id="startButton" onclick="startGame()">Начать игру</button>

        <br><br>

        <input type="number" id="userGuess" placeholder="Ваше число" style="display:none;">
        
        <br><br>

        <button type="button" id="guessButton" style="display:none;" onclick="guessNumber()">Угадать</button>

    </form>

    <p id="resultMessage"></p>

</div>


<script>

    let randomNumber;

    let attempts = 0;

    const maxAttempts = 3;


    function startGame() {

        randomNumber = Math.floor(Math.random() * 51); // Генерация случайного числа от 0 до 50

        attempts = 0; // Сбрасываем количество попыток

        document.getElementById('startButton').style.display = 'none';

        document.getElementById('userGuess').style.display = 'inline';

        document.getElementById('guessButton').style.display = 'inline';

    }


    function guessNumber() {

        const guess = parseInt(document.getElementById('userGuess').value);

        attempts++; // Увеличиваем счетчик попыток


        if (guess === randomNumber) {

            document.getElementById('resultMessage').innerText = 'Успех! Вы угадали число ' + randomNumber + '!';

            resetGame();

        } else {

            const remainingAttempts = maxAttempts - attempts;

            if (remainingAttempts > 0) {

                if (guess < randomNumber) {

                    document.getElementById('resultMessage').innerText = `Потрачено! Загаданное число больше, чем ${guess}. Осталось ${remainingAttempts} попыток.`;

                } else {

                    document.getElementById('resultMessage').innerText = `Потрачено! Загаданное число меньше, чем ${guess}. Осталось ${remainingAttempts} попыток.`;

                }
                

            } else {

                document.getElementById('resultMessage').innerText = 'Игра окончена! Правильное число было ' + randomNumber + '.';

                resetGame();

            }

        }

    }
    
    function resetGame() {

        document.getElementById('userGuess').style.display = 'none';

        document.getElementById('guessButton').style.display = 'none';

        document.getElementById('startButton').style.display = 'inline';

        document.getElementById('startButton').innerText = 'Начать игру снова';

    }
</script>


!!! note

    У вас есть 3 попытки, чтобы угадать число от 0 до 50