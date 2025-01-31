# beeer
beeer
/beer_game
  /index.html
  /style.css
  /script.js

<!DOCTYPE html>
<html lang="uk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Гра в Пиво</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header>
        <h1>Гра в Пиво</h1>
    </header>

    <main>
        <section class="game">
            <h2>Вибери пиво!</h2>
            <div class="beer-buttons">
                <button class="beer" data-beer="lager">Лагер</button>
                <button class="beer" data-beer="ale">Ель</button>
                <button class="beer" data-beer="stout">Стаут</button>
            </div>
            <p id="result"></p>
        </section>
    </main>

    <footer>
        <p>&copy; 2025 Гра в Пиво</p>
    </footer>

    <script src="script.js"></script>
</body>
</html>

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: Arial, sans-serif;
    background-color: #f0f0f0;
    color: #333;
    text-align: center;
}

header {
    background-color: #ffcc00;
    padding: 20px;
    color: white;
}

h1 {
    font-size: 2.5rem;
}

main {
    padding: 40px;
}

.game {
    background-color: #fff;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    padding: 30px;
}

h2 {
    font-size: 1.5rem;
    margin-bottom: 20px;
}

.beer-buttons {
    margin-bottom: 20px;
}

.beer {
    padding: 15px 30px;
    margin: 10px;
    font-size: 1rem;
    background-color: #ffcc00;
    border: none;
    cursor: pointer;
    border-radius: 5px;
}

.beer:hover {
    background-color: #e6b800;
}

footer {
    padding: 20px;
    background-color: #ffcc00;
    color: white;
}

// Массив пив
const beers = ["lager", "ale", "stout"];

// Генерація випадкового пива
function getRandomBeer() {
    const randomIndex = Math.floor(Math.random() * beers.length);
    return beers[randomIndex];
}

// Оновлення результату гри
function displayResult(selectedBeer, correctBeer) {
    const resultElement = document.getElementById('result');
    if (selectedBeer === correctBeer) {
        resultElement.textContent = "Правильно! Це " + correctBeer.toUpperCase() + "!";
        resultElement.style.color = "green";
    } else {
        resultElement.textContent = "Неправильно! Спробуйте ще раз!";
        resultElement.style.color = "red";
    }
}

// Додавання слухачів подій для кнопок
const beerButtons = document.querySelectorAll('.beer');
beerButtons.forEach(button => {
    button.addEventListener('click', function() {
        const selectedBeer = this.getAttribute('data-beer');
        const correctBeer = getRandomBeer();
        displayResult(selectedBeer, correctBeer);
    });
});
