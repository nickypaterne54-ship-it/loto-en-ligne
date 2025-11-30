<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Loto en Ligne</title>
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #1a2a6c, #b21f1f, #fdbb2d);
            color: white;
            min-height: 100vh;
            padding: 20px;
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        
        .container {
            max-width: 800px;
            width: 100%;
            background-color: rgba(0, 0, 0, 0.7);
            border-radius: 15px;
            padding: 30px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
            margin-top: 20px;
        }
        
        h1 {
            text-align: center;
            margin-bottom: 20px;
            font-size: 2.5rem;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
        }
        
        .game-info {
            display: flex;
            justify-content: space-between;
            margin-bottom: 20px;
            background-color: rgba(255, 255, 255, 0.1);
            padding: 15px;
            border-radius: 10px;
        }
        
        .info-item {
            text-align: center;
        }
        
        .info-value {
            font-size: 1.5rem;
            font-weight: bold;
            color: #fdbb2d;
        }
        
        .grid-container {
            display: flex;
            flex-wrap: wrap;
            gap: 15px;
            margin-bottom: 30px;
        }
        
        .number-grid {
            flex: 1;
            min-width: 300px;
            display: grid;
            grid-template-columns: repeat(5, 1fr);
            gap: 10px;
            padding: 15px;
            background-color: rgba(255, 255, 255, 0.1);
            border-radius: 10px;
        }
        
        .number {
            width: 50px;
            height: 50px;
            display: flex;
            align-items: center;
            justify-content: center;
            background-color: #2c3e50;
            border-radius: 50%;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s;
            user-select: none;
        }
        
        .number:hover {
            transform: scale(1.1);
            background-color: #3498db;
        }
        
        .selected {
            background-color: #e74c3c;
            transform: scale(1.1);
        }
        
        .drawn {
            background-color: #2ecc71;
            transform: scale(1.1);
        }
        
        .controls {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin-bottom: 20px;
        }
        
        button {
            padding: 12px 25px;
            border: none;
            border-radius: 50px;
            font-size: 1rem;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s;
            background-color: #3498db;
            color: white;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.2);
        }
        
        button:hover {
            transform: translateY(-3px);
            box-shadow: 0 6px 8px rgba(0, 0, 0, 0.3);
        }
        
        button:active {
            transform: translateY(1px);
        }
        
        #play-btn {
            background-color: #2ecc71;
        }
        
        #reset-btn {
            background-color: #e74c3c;
        }
        
        .results {
            margin-top: 20px;
            padding: 20px;
            background-color: rgba(255, 255, 255, 0.1);
            border-radius: 10px;
            text-align: center;
        }
        
        .drawn-numbers {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 10px;
            margin: 20px 0;
        }
        
        .drawn-number {
            width: 50px;
            height: 50px;
            display: flex;
            align-items: center;
            justify-content: center;
            background-color: #2ecc71;
            border-radius: 50%;
            font-weight: bold;
            animation: pop 0.5s;
        }
        
        @keyframes pop {
            0% { transform: scale(0); }
            70% { transform: scale(1.2); }
            100% { transform: scale(1); }
        }
        
        .message {
            font-size: 1.5rem;
            margin-top: 15px;
            padding: 10px;
            border-radius: 10px;
            background-color: rgba(255, 255, 255, 0.1);
        }
        
        .win {
            color: #2ecc71;
            font-weight: bold;
            animation: pulse 1s infinite;
        }
        
        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.05); }
            100% { transform: scale(1); }
        }
        
        .rules {
            margin-top: 30px;
            padding: 20px;
            background-color: rgba(255, 255, 255, 0.1);
            border-radius: 10px;
        }
        
        .rules h2 {
            margin-bottom: 15px;
            text-align: center;
        }
        
        .rules ul {
            padding-left: 20px;
        }
        
        .rules li {
            margin-bottom: 10px;
            line-height: 1.5;
        }
        
        @media (max-width: 600px) {
            .game-info {
                flex-direction: column;
                gap: 10px;
            }
            
            .controls {
                flex-direction: column;
            }
            
            button {
                width: 100%;
            }
        }
    </style>
</head>
<body>
    <h1>🎱 LOTO EN LIGNE 🎱</h1>
    
    <div class="container">
        <div class="game-info">
            <div class="info-item">
                <div>Numéros sélectionnés</div>
                <div class="info-value" id="selected-count">0/5</div>
            </div>
            <div class="info-item">
                <div>Gains</div>
                <div class="info-value" id="winnings">0 €</div>
            </div>
            <div class="info-item">
                <div>Parties jouées</div>
                <div class="info-value" id="games-played">0</div>
            </div>
        </div>
        
        <div class="grid-container">
            <div class="number-grid" id="main-numbers">
                <!-- Les numéros principaux seront générés par JavaScript -->
            </div>
        </div>
        
        <div class="controls">
            <button id="play-btn">Jouer</button>
            <button id="reset-btn">Réinitialiser</button>
        </div>
        
        <div class="results" id="results" style="display: none;">
            <h2>Résultats du tirage</h2>
            <div class="drawn-numbers" id="drawn-numbers">
                <!-- Les numéros tirés seront affichés ici -->
            </div>
            <div class="message" id="result-message">
                <!-- Le message de résultat sera affiché ici -->
            </div>
        </div>
        
        <div class="rules">
            <h2>Règles du jeu</h2>
            <ul>
                <li>Sélectionnez 5 numéros entre 1 et 50</li>
                <li>Cliquez sur "Jouer" pour lancer le tirage</li>
                <li>Le système tire 5 numéros au hasard</li>
                <li>Plus vous avez de numéros correspondants, plus vous gagnez !</li>
                <li>Gains : 2 numéros = 2€, 3 numéros = 10€, 4 numéros = 100€, 5 numéros = 1000€</li>
            </ul>
        </div>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            // Éléments du DOM
            const mainNumbersGrid = document.getElementById('main-numbers');
            const selectedCountElement = document.getElementById('selected-count');
            const winningsElement = document.getElementById('winnings');
            const gamesPlayedElement = document.getElementById('games-played');
            const playButton = document.getElementById('play-btn');
            const resetButton = document.getElementById('reset-btn');
            const resultsElement = document.getElementById('results');
            const drawnNumbersElement = document.getElementById('drawn-numbers');
            const resultMessageElement = document.getElementById('result-message');
            
            // Variables du jeu
            let selectedNumbers = [];
            let winnings = 0;
            let gamesPlayed = 0;
            
            // Initialiser la grille de numéros
            function initializeNumberGrid() {
                mainNumbersGrid.innerHTML = '';
                
                for (let i = 1; i <= 50; i++) {
                    const numberElement = document.createElement('div');
                    numberElement.className = 'number';
                    numberElement.textContent = i;
                    numberElement.dataset.number = i;
                    
                    numberElement.addEventListener('click', function() {
                        toggleNumberSelection(i, numberElement);
                    });
                    
                    mainNumbersGrid.appendChild(numberElement);
                }
            }
            
            // Basculer la sélection d'un numéro
            function toggleNumberSelection(number, element) {
                const index = selectedNumbers.indexOf(number);
                
                if (index === -1) {
                    // Sélectionner le numéro
                    if (selectedNumbers.length < 5) {
                        selectedNumbers.push(number);
                        element.classList.add('selected');
                    }
                } else {
                    // Désélectionner le numéro
                    selectedNumbers.splice(index, 1);
                    element.classList.remove('selected');
                }
                
                updateSelectedCount();
            }
            
            // Mettre à jour le compteur de numéros sélectionnés
            function updateSelectedCount() {
                selectedCountElement.textContent = ${selectedNumbers.length}/5;
                
                // Activer/désactiver le bouton Jouer
                playButton.disabled = selectedNumbers.length !== 5;
            }
            
            // Générer des numéros aléatoires pour le tirage
            function generateRandomNumbers(count, min, max) {
                const numbers = [];
                while (numbers.length < count) {
                    const randomNumber = Math.floor(Math.random() * (max - min + 1)) + min;
                    if (!numbers.includes(randomNumber)) {
                        numbers.push(randomNumber);
                    }
                }
                return numbers.sort((a, b) => a - b);
            }
            
            // Jouer une partie
            function playGame() {
                if (selectedNumbers.length !== 5) return;
                
                // Générer les numéros du tirage
                const drawnNumbers = generateRandomNumbers(5, 1, 50);
                
                // Afficher les résultats
                displayResults(drawnNumbers);
                
                // Calculer les gains
                calculateWinnings(drawnNumbers);
                
                // Mettre à jour les statistiques
                gamesPlayed++;
                gamesPlayedElement.textContent = gamesPlayed;
                
                // Désactiver la sélection des numéros pendant l'affichage des résultats
                disableNumberSelection();
            }
            
            // Afficher les résultats du tirage
            function displayResults(drawnNumbers) {
                // Afficher la section des résultats
                resultsElement.style.display = 'block';
                
                // Afficher les numéros tirés
                drawnNumbersElement.innerHTML = '';
                drawnNumbers.forEach(number => {
                    const numberElement = document.createElement('div');
                    numberElement.className = 'drawn-number';
                    numberElement.textContent = number;
                    drawnNumbersElement.appendChild(numberElement);
                    
                    // Marquer les numéros correspondants
                    if (selectedNumbers.includes(number)) {
                        const selectedElement = document.querySelector(.number[data-number="${number}"]);
                        selectedElement.classList.add('drawn');
                    }
                });
                
                // Faire défiler jusqu'aux résultats
                resultsElement.scrollIntoView({ behavior: 'smooth' });
            }
            
            // Calculer les gains
            function calculateWinnings(drawnNumbers) {
                // Compter les correspondances
                let matches = 0;
                selectedNumbers.forEach(number => {
                    if (drawnNumbers.includes(number)) {
                        matches++;
                    }
                });
                
                // Déterminer les gains selon le nombre de correspondances
                let winAmount = 0;
                let message = '';
                
                switch (matches) {
                    case 2:
                        winAmount = 2;
                        message = 'Félicitations ! Vous avez 2 numéros gagnants !';
                        break;
                    case 3:
                        winAmount = 10;
                        message = 'Bravo ! Vous avez 3 numéros gagnants !';
                        break;
                    case 4:
                        winAmount = 100;
                        message = 'Incroyable ! Vous avez 4 numéros gagnants !';
                        break;
                    case 5:
                        winAmount = 1000;
                        message = 'JACKPOT ! Vous avez tous les numéros gagnants !';
                        break;
                    default:
                        message = 'Désolé, vous n\'avez pas gagné cette fois. Essayez encore !';
                }
                
                // Mettre à jour les gains totaux
                winnings += winAmount;
                winningsElement.textContent = ${winnings} €;
                
                // Afficher le message de résultat
                resultMessageElement.textContent = message;
                resultMessageElement.className = 'message';
                if (matches >= 2) {
                    resultMessageElement.classList.add('win');
                }
            }
            
            // Désactiver la sélection des numéros
            function disableNumberSelection() {
                const numberElements = document.querySelectorAll('.number');
                numberElements.forEach(element => {
                    element.style.pointerEvents = 'none';
                });
                
                playButton.disabled = true;
            }
            
            // Activer la sélection des numéros
            function enableNumberSelection() {
                const numberElements = document.querySelectorAll('.number');
                numberElements.forEach(element => {
                    element.style.pointerEvents = 'auto';
                });
                
                updateSelectedCount();
            }
            
            // Réinitialiser le jeu
            function resetGame() {
                selectedNumbers = [];
                
                // Réinitialiser l'interface
                const numberElements = document.querySelectorAll('.number');
                numberElements.forEach(element => {
                    element.classList.remove('selected', 'drawn');
                });
                
                // Cacher les résultats
                resultsElement.style.display = 'none';
                
                // Réactiver la sélection
                enableNumberSelection();
            }
            
            // Événements des boutons
            playButton.addEventListener('click', playGame);
            resetButton.addEventListener('click', resetGame);
            
            // Initialiser le jeu
            initializeNumberGrid();
            updateSelectedCount();
        });
    </script>
</body>
</html>
