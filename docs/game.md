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

        display: flex; /* Используем flexbox для размещения элементов */

        flex-direction: column; /* Располагаем элементы по вертикали */

        align-items: center; /* Центрируем элементы по горизонтали */

    }


    .guess-form input {

        padding: 10px;

        width: 100%;

        max-width: 300px; /* Ограничиваем максимальную ширину до 300px */

        font-size: 18px;

        border: 2px solid #007BFF;

        border-radius: 5px;

        background-color: #f8f9fa;

        box-shadow: 2px 2px 5px rgba(0, 0, 0, 0.1);

        transition: border-color 0.3s;

    }


    .guess-form input:focus {

        border-color: #0056b3;

        outline: none;

    }


    .guess-form button {

        padding: 10px 20px;

        background-color: #007BFF;

        color: white;

        border: none;

        border-radius: 5px; /* Скругленные углы кнопки */

        cursor: pointer;

        font-size: 18px;

        min-width: 150px; /* Минимальная ширина кнопки */

        margin: 5px; /* Отступ между кнопками */

        transition: background-color 0.3s; /* Плавный переход цвета фона */

    }


    .guess-form button:hover {

        background-color: #0056b3;

    }

</style>


<div class="container">

    <form class="guess-form" id="guessForm">

        <button type="button" id="startButton" onclick="startGame()">Начать игру</button>

        <input type="number" id="userGuess" placeholder="Ваше число" style="display:none;">

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