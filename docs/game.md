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
        width: 100px;
    }
    .guess-form button {
        padding: 10px 20px;
        background-color: #007BFF;
        color: white;
        border: none;
        cursor: pointer;
    }
    .guess-form button:hover {
        background-color: #0056b3;
    }
</style>

<div class="container">
    <form class="guess-form" id="guessForm">
        <button type="button" onclick="guessNumber()">Начать игру</button>
    </form>
    <p id="resultMessage"></p>
</div>

!!! note
    У вас есть 3 попытки, чтобы угадать число от 0 до 50