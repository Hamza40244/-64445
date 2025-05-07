<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>لعبة الساموراي ضد الوحش</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div id="gameContainer">
        <div id="samurai"></div>
        <div id="monster" onclick="attackMonster()"></div>
        <div id="healthBar"></div>
        <div id="score">النتيجة: 0</div>
    </div>

    <script src="game.js"></script>
</body>
</html>
body {
    background-color: #2f2f2f;
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
}

#gameContainer {
    width: 100%;
    height: 100vh;
    position: relative;
    overflow: hidden;
}

#samurai {
    width: 50px;
    height: 100px;
    background-color: blue;
    position: absolute;
    bottom: 0;
    left: 100px;
}

#monster {
    width: 100px;
    height: 150px;
    background-color: red;
    position: absolute;
    bottom: 0;
    right: 100px;
    cursor: pointer;
}

#healthBar {
    position: absolute;
    top: 10px;
    left: 10px;
    width: 200px;
    height: 20px;
    background-color: #333;
}

#healthBar:before {
    content: '';
    display: block;
    width: 100%;
    height: 100%;
    background-color: green;
}

#score {
    position: absolute;
    top: 10px;
    right: 10px;
    color: white;
    font-size: 20px;
let samurai = document.getElementById('samurai');
let monster = document.getElementById('monster');
let healthBar = document.getElementById('healthBar');
let scoreElement = document.getElementById('score');
let health = 100;
let score = 0;

// الهجوم على الوحش
function attackMonster() {
    if (health > 0) {
        score += 10;
        scoreElement.innerHTML = "النتيجة: " + score;
        moveMonster();
    }
}

// تحريك الوحش بشكل عشوائي
function moveMonster() {
    let randomPositionX = Math.floor(Math.random() * (window.innerWidth - 100));
    let randomPositionY = Math.floor(Math.random() * (window.innerHeight - 150));
    monster.style.left = randomPositionX + 'px';
    monster.style.bottom = randomPositionY + 'px';

    // وحش يهاجم الساموراي
    monsterAttack();
}

// الهجوم من الوحش
function monsterAttack() {
    let randomAttack = Math.random();
    if (randomAttack < 0.3) {
        health -= 10;
        healthBar.style.width = health + '%';
        if (health <= 0) {
            alert('لقد خس
