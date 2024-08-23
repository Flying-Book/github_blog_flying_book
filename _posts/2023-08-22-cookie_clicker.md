---
layout: post
title: Cookie Clicker Game
description: Cookie Clicker game 
permalink: /cookie_clicker
toc: true
comments: true
---
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cookie Clicker</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #87CEEB;
            background-image: linear-gradient(to top, #87CEEB, #FFFFFF);
            margin: 0;
            padding: 0;
        }

        #game {
            margin-top: 50px;
        }

        #cookie {
            width: 200px;
            cursor: pointer;
            border-radius: 50%;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
        }

        #shop {
            margin-top: 20px;
            padding: 20px;
            background-color: #FFFFFF;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
            border-radius: 10px;
            display: inline-block;
        }

        .shop-item {
            margin: 10px 0;
        }

        #shop h2 {
            margin: 0 0 10px;
        }

        .shop-item button {
            padding: 10px 20px;
            background-color: #FFD700;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-weight: bold;
            color: #000;
            transition: background-color 0.3s;
        }

        .shop-item button:hover {
            background-color: #FFC107;
        }
    </style>
</head>
<body>
    <div id="game">
        <h1>Cookie Clicker</h1>
        <p>Cookies: <span id="cookie-count">0</span></p>
        <img id="cookie" src="https://upload.wikimedia.org/wikipedia/commons/6/69/Chocolate_Chip_Cookies_-_kimberlykv.jpg" alt="Cookie">
        <div id="shop">
            <h2>Shop</h2>
            <div class="shop-item">
                <button id="worker-btn">Buy Worker (10 cookies)</button>
                <p>Workers: <span id="worker-count">0</span></p>
            </div>
            <div class="shop-item">
                <button id="grandma-btn">Buy Grandma (50 cookies)</button>
                <p>Grandmas: <span id="grandma-count">0</span></p>
            </div>
            <div class="shop-item">
                <button id="factory-btn">Buy Factory (200 cookies)</button>
                <p>Factories: <span id="factory-count">0</span></p>
            </div>
        </div>
    </div>
    <audio id="click-sound" src="https://www.soundjay.com/button/sounds/button-16.mp3"></audio>
    <script>
        let cookieCount = 0;
        let workerCount = 0;
        let grandmaCount = 0;
        let factoryCount = 0;

        const workerCost = 10;
        const grandmaCost = 50;
        const factoryCost = 200;

        const workerRate = 1; // Cookies per second per worker
        const grandmaRate = 5; // Cookies per second per grandma
        const factoryRate = 20; // Cookies per second per factory

        const cookieDisplay = document.getElementById('cookie-count');
        const workerDisplay = document.getElementById('worker-count');
        const grandmaDisplay = document.getElementById('grandma-count');
        const factoryDisplay = document.getElementById('factory-count');

        const cookieElement = document.getElementById('cookie');
        const workerButton = document.getElementById('worker-btn');
        const grandmaButton = document.getElementById('grandma-btn');
        const factoryButton = document.getElementById('factory-btn');
        const clickSound = document.getElementById('click-sound');

        // Function to update cookie count display
        function updateCookieCount() {
            cookieDisplay.textContent = cookieCount;
        }

        // Function to update worker count display
        function updateWorkerCount() {
            workerDisplay.textContent = workerCount;
        }

        // Function to update grandma count display
        function updateGrandmaCount() {
            grandmaDisplay.textContent = grandmaCount;
        }

        // Function to update factory count display
        function updateFactoryCount() {
            factoryDisplay.textContent = factoryCount;
        }

        // Function to handle cookie click
        cookieElement.addEventListener('click', () => {
            cookieCount++;
            updateCookieCount();
            clickSound.play();
        });

        // Function to handle worker purchase
        workerButton.addEventListener('click', () => {
            if (cookieCount >= workerCost) {
                cookieCount -= workerCost;
                workerCount++;
                updateCookieCount();
                updateWorkerCount();
            }
        });

        // Function to handle grandma purchase
        grandmaButton.addEventListener('click', () => {
            if (cookieCount >= grandmaCost) {
                cookieCount -= grandmaCost;
                grandmaCount++;
                updateCookieCount();
                updateGrandmaCount();
            }
        });

        // Function to handle factory purchase
        factoryButton.addEventListener('click', () => {
            if (cookieCount >= factoryCost) {
                cookieCount -= factoryCost;
                factoryCount++;
                updateCookieCount();
                updateFactoryCount();
            }
        });

        // Function to passively increase cookies from workers, grandmas, and factories
        setInterval(() => {
            cookieCount += workerCount * workerRate;
            cookieCount += grandmaCount * grandmaRate;
            cookieCount += factoryCount * factoryRate;
            updateCookieCount();
        }, 1000);
    </script>
</body>
</html>
