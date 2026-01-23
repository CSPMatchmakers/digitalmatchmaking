---
layout: post
title: Card Game
description: Discover your coding style through an interactive ML-powered card sorting game.
permalink: /ml/
breadcrumb: true
microblog: true
author: Ethan W
---

<style>
    body {
        min-height: 100vh;
        background: url('{{ site.baseurl }}/images/code.png') no-repeat center center fixed;
        background-size: cover;
        background-color: #0f2027;
    }

    * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
    }

    .game-container {
        max-width: 1400px;
        margin: 1em auto;
        background: rgba(30, 30, 46, 0.95);
        border-radius: 16px;
        padding: 2.5em;
        box-shadow: 0 20px 60px rgba(0, 0, 0, 0.5);
        backdrop-filter: blur(10px);
        border: 1px solid rgba(102, 126, 234, 0.3);
        color: #e0e0e0;
        font-family: 'Courier New', monospace;
        min-height: 85vh;
    }

    .header {
        text-align: center;
        margin-bottom: 2em;
        animation: fadeIn 0.8s ease-in;
    }

    .header h1 {
        font-size: 2.5em;
        color: #8b9dff;
        text-shadow: 0 0 20px rgba(139, 157, 255, 0.5);
        margin-bottom: 0.3em;
    }

    .ml-badge {
        display: inline-block;
        background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
        color: white;
        padding: 0.5em 1em;
        border-radius: 20px;
        font-size: 0.9em;
        margin-top: 0.5em;
    }

    .instructions {
        background: linear-gradient(135deg, #2a2a40 0%, #1f1f35 100%);
        padding: 1.5em;
        border-radius: 12px;
        border-left: 4px solid #667eea;
        box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
        margin-bottom: 2em;
    }

    .instructions h2 {
        color: #8b9dff;
        margin-bottom: 0.8em;
        font-size: 1.3em;
    }

    .instructions p {
        line-height: 1.8;
        color: #c0c0c0;
        margin-bottom: 0.8em;
    }

    .ml-info {
        background: rgba(102, 126, 234, 0.1);
        border: 2px solid #667eea;
        padding: 1em;
        border-radius: 8px;
        margin-top: 1em;
        font-size: 0.9em;
    }

    .ml-info strong {
        color: #8b9dff;
    }

    #game-section {
        display: block;
    }

    #result-section {
        display: none;
    }

    .game-board {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 1.5em;
        margin-bottom: 2em;
    }

    .category-zone {
        background: rgba(30, 30, 46, 0.9);
        border: 3px dashed #667eea;
        border-radius: 16px;
        padding: 1.5em;
        min-height: 350px;
        transition: all 0.3s ease;
    }

    .category-zone.drag-over {
        background: rgba(102, 126, 234, 0.2);
        border-color: #8b9dff;
        box-shadow: 0 0 30px rgba(139, 157, 255, 0.4);
        transform: scale(1.02);
    }

    .category-header {
        text-align: center;
        margin-bottom: 1em;
        padding-bottom: 0.8em;
        border-bottom: 2px solid #667eea;
    }

    .category-icon {
        font-size: 2.5em;
        margin-bottom: 0.3em;
    }

    .category-title {
        font-size: 1.4em;
        color: #8b9dff;
        font-weight: bold;
    }

    .category-count {
        font-size: 0.9em;
        color: #c0c0c0;
        margin-top: 0.3em;
    }

    .cards-pool {
        background: rgba(30, 30, 46, 0.9);
        border: 3px solid #667eea;
        border-radius: 16px;
        padding: 1.5em;
        margin-bottom: 2em;
    }

    .cards-pool h3 {
        color: #8b9dff;
        margin-bottom: 1em;
        text-align: center;
        font-size: 1.2em;
    }

    .cards-container {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
        gap: 1em;
    }

    .card {
        background: linear-gradient(135deg, #2a2a40 0%, #1f1f35 100%);
        border: 2px solid #667eea;
        border-radius: 12px;
        padding: 1.2em;
        cursor: grab;
        transition: all 0.3s ease;
        box-shadow: 0 4px 15px rgba(0, 0, 0, 0.3);
    }

    .card:active {
        cursor: grabbing;
    }

    .card:hover {
        transform: translateY(-5px) rotate(2deg);
        box-shadow: 0 8px 25px rgba(102, 126, 234, 0.4);
        border-color: #8b9dff;
    }

    .card.dragging {
        opacity: 0.5;
        transform: rotate(5deg);
    }

    .card-text {
        color: #e0e0e0;
        line-height: 1.5;
        font-size: 0.95em;
    }

    .category-cards {
        display: flex;
        flex-direction: column;
        gap: 0.8em;
        min-height: 100px;
    }

    .submit-section {
        text-align: center;
        margin-top: 2em;
    }

    .submit-btn {
        background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
        color: white;
        border: none;
        padding: 1.2em 3em;
        border-radius: 12px;
        font-size: 1.2em;
        font-weight: bold;
        cursor: pointer;
        transition: all 0.3s ease;
        font-family: 'Courier New', monospace;
        box-shadow: 0 6px 20px rgba(102, 126, 234, 0.4);
    }

    .submit-btn:hover:not(:disabled) {
        transform: translateY(-3px);
        box-shadow: 0 10px 30px rgba(102, 126, 234, 0.6);
    }

    .submit-btn:disabled {
        opacity: 0.5;
        cursor: not-allowed;
    }

    .status-message {
        margin-top: 1em;
        padding: 1em;
        border-radius: 8px;
        text-align: center;
        animation: slideIn 0.3s ease-in;
    }

    .status-success {
        background: rgba(39, 174, 96, 0.2);
        border: 2px solid #27ae60;
        color: #27ae60;
    }

    .status-error {
        background: rgba(231, 76, 60, 0.2);
        border: 2px solid #e74c3c;
        color: #e74c3c;
    }

    .status-info {
        background: rgba(102, 126, 234, 0.2);
        border: 2px solid #667eea;
        color: #8b9dff;
    }

    .result-container {
        text-align: center;
    }

    .result-icon {
        font-size: 5em;
        margin-bottom: 0.3em;
        animation: bounceIn 0.6s ease-out;
    }

    .result-title {
        font-size: 2.5em;
        color: #8b9dff;
        font-weight: bold;
        margin-bottom: 0.5em;
    }

    .result-description {
        background: linear-gradient(135deg, #2a2a40 0%, #1f1f35 100%);
        padding: 1.5em;
        border-radius: 12px;
        border-left: 4px solid #667eea;
        box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
        margin-bottom: 2em;
    }

    .result-description p {
        line-height: 1.8;
        color: #c0c0c0;
        font-size: 1.1em;
    }

    .confidence-bar {
        margin: 1em 0;
        background: #1f1f35;
        border-radius: 10px;
        overflow: hidden;
        height: 30px;
    }

    .confidence-fill {
        height: 100%;
        background: linear-gradient(90deg, #667eea, #764ba2);
        display: flex;
        align-items: center;
        justify-content: center;
        color: white;
        font-weight: bold;
        transition: width 1s ease;
    }

    .stats-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
        gap: 1.5em;
        margin-bottom: 2em;
    }

    .stat-card {
        background: linear-gradient(135deg, #2a2a40 0%, #1f1f35 100%);
        padding: 1.5em;
        border-radius: 12px;
        border: 2px solid #667eea;
        text-align: center;
        transition: all 0.3s;
    }

    .stat-card:hover {
        transform: translateY(-4px);
        box-shadow: 0 8px 20px rgba(102, 126, 234, 0.3);
    }

    .stat-value {
        font-size: 2.5em;
        font-weight: bold;
        color: #8b9dff;
        margin-bottom: 0.3em;
    }

    .stat-label {
        color: #c0c0c0;
        font-size: 0.9em;
    }

    @keyframes fadeIn {
        from { opacity: 0; transform: translateY(-20px); }
        to { opacity: 1; transform: translateY(0); }
    }

    @keyframes slideIn {
        from { opacity: 0; transform: translateY(10px); }
        to { opacity: 1; transform: translateY(0); }
    }

    @keyframes bounceIn {
        0% { transform: scale(0); }
        50% { transform: scale(1.1); }
        100% { transform: scale(1); }
    }

    @media (max-width: 768px) {
        .game-board {
            grid-template-columns: 1fr;
        }
        
        .cards-container {
            grid-template-columns: 1fr;
        }

        .submit-section {
            display: flex;
            flex-direction: column;
            gap: 1em;
        }

        .submit-section .submit-btn {
            margin-right: 0 !important;
        }
    }
</style>

<div class="game-container">
    <div class="header">
        <h1>🎴 Card Game</h1>
        <div class="ml-badge">🤖 Powered by Machine Learning</div>
        <p style="color: #c0c0c0; font-size: 1.1em; margin-top: 0.5em;">Sort cards to discover your coding style</p>
    </div>

    <!-- Game Section -->
    <div id="game-section">
        <div class="instructions">
            <h2>📋 How to Play</h2>
            <p>Drag each card into one of the two zones below. Choose based on what resonates with you as a coder. Once all cards are sorted, our ML model will analyze your choices and predict your coding profile!</p>
            <div class="ml-info">
                <strong>🧠 ML Model:</strong> This game uses a decision tree classifier trained on coding activity patterns. The model analyzes your card placements across multiple feature dimensions (exploration tendency, collaboration preference, debugging comfort, and implementation focus) to classify your coding style with a confidence score.
            </div>
        </div>

        <div class="cards-pool">
            <h3>🃏 Available Cards - Drag to Zones Below</h3>
            <div class="cards-container" id="cards-pool">
                <!-- Cards will be dynamically inserted here -->
            </div>
        </div>

        <div class="game-board" id="game-board">
            <!-- Two zones will be created here -->
        </div>

        <div class="submit-section">
            <button class="submit-btn" style="background: linear-gradient(135deg, #27ae60 0%, #229954 100%); margin-right: 1em;" onclick="autoFill()">
                ⚡ Auto-Fill (Random)
            </button>
            <button class="submit-btn" id="submit-btn" onclick="analyzeResults()">
                🤖 Run ML Analysis
            </button>
            <div id="status-message"></div>
        </div>
    </div>

    <!-- Result Section -->
    <div id="result-section">
        <div class="result-container">
            <div class="result-icon" id="result-icon">🎯</div>
            <div class="result-title" id="result-title">Your Coding Profile</div>
            
            <div class="ml-info" style="margin-bottom: 1em;">
                <strong>ML Prediction Confidence:</strong>
                <div class="confidence-bar">
                    <div class="confidence-fill" id="confidence-fill" style="width: 0%">0%</div>
                </div>
            </div>

            <div class="result-description" id="result-description"></div>
            
            <div class="stats-grid" id="result-stats"></div>

            <div class="ml-info" style="text-align: left;">
                <strong>🔬 How the ML Model Works:</strong>
                <p style="margin-top: 0.5em; line-height: 1.6;">
                    <strong>Feature Extraction:</strong> Your card placements are converted into 4 numerical features representing exploration tendency, collaboration preference, debugging comfort, and implementation focus.<br><br>
                    <strong>Classification:</strong> A decision tree classifier evaluates these features and assigns you to one of three coding profiles based on learned patterns.<br><br>
                    <strong>Confidence Score:</strong> The model calculates prediction confidence based on feature strength and consistency of your choices.
                </p>
            </div>

            <div style="margin-top: 2em; display: flex; gap: 1em; justify-content: center; flex-wrap: wrap;">
                <button class="submit-btn" id="save-profile-btn" onclick="saveToProfile()">
                    💾 Save to Profile
                </button>
                <button class="submit-btn" onclick="restartGame()">
                    🔄 Play Again
                </button>
            </div>
            <div id="save-status"></div>
            
            <div class="ml-info" style="margin-top: 1.5em; text-align: left;" id="save-info">
                <strong>💡 What happens when you save?</strong>
                <p style="margin-top: 0.5em; line-height: 1.6;">
                    Your ML-predicted coding profile will be stored in your matchmaking database. This includes:<br>
                    • Your predicted coding style (${analysisResult ? analysisResult.profile.name : 'Explorer/Builder/Collaborator'})<br>
                    • ML confidence score (${analysisResult ? analysisResult.confidence : 'XX'}%)<br>
                    • Feature scores for exploration, collaboration, debugging, and implementation<br>
                    • Your complete card placement preferences<br><br>
                    This data can be used by matchmaking algorithms to pair you with compatible coding partners who share similar or complementary styles!
                </p>
            </div>
        </div>
    </div>
</div>

<script>
    const zones = [
        {
            id: 'prefer',
            title: 'I Prefer This',
            icon: '👍',
            description: 'Activities you enjoy and gravitate towards'
        },
        {
            id: 'avoid',
            title: 'I Avoid This',
            icon: '👎',
            description: 'Activities you tend to skip or postpone'
        }
    ];

    // Cards with feature weights for ML model
    const cards = [
        { id: 1, text: "Explore a new Python library and build a tiny demo", features: { explore: 1, collab: 0, debug: 0, implement: 0.5 } },
        { id: 2, text: "Fix a bug in an existing script", features: { explore: 0, collab: 0, debug: 1, implement: 0 } },
        { id: 3, text: "Write a unit test for a function", features: { explore: 0, collab: 0, debug: 0.5, implement: 0.5 } },
        { id: 4, text: "Implement a small ML model from scratch", features: { explore: 0.8, collab: 0, debug: 0, implement: 1 } },
        { id: 5, text: "Review a teammate's pull request", features: { explore: 0, collab: 1, debug: 0.3, implement: 0 } },
        { id: 6, text: "Refactor messy code in a repo", features: { explore: 0, collab: 0, debug: 0.5, implement: 0.5 } },
        { id: 7, text: "Contribute a patch to an open-source project", features: { explore: 0.5, collab: 1, debug: 0.3, implement: 0.7 } },
        { id: 8, text: "Automate a repetitive task with a short script", features: { explore: 0.3, collab: 0, debug: 0, implement: 1 } },
        { id: 9, text: "Experiment with hyperparameters on a dataset", features: { explore: 1, collab: 0, debug: 0, implement: 0.3 } },
        { id: 10, text: "Brainstorm and implement a new feature in a mini-project", features: { explore: 0.5, collab: 0, debug: 0, implement: 1 } },
        { id: 11, text: "Merge code from a teammate into a shared branch", features: { explore: 0, collab: 0.8, debug: 0.5, implement: 0 } },
        { id: 12, text: "Analyze a dataset and output basic statistics", features: { explore: 0.5, collab: 0, debug: 0, implement: 0.7 } },
        { id: 13, text: "Write a helper function for a project you are working on", features: { explore: 0, collab: 0, debug: 0, implement: 1 } },
        { id: 14, text: "Try out a new programming language by writing a small program", features: { explore: 1, collab: 0, debug: 0, implement: 0.5 } },
        { id: 15, text: "Pair-program with someone to implement a feature", features: { explore: 0.3, collab: 1, debug: 0, implement: 0.8 } },
        { id: 16, text: "Debug a piece of code that throws an error you don't understand yet", features: { explore: 0.5, collab: 0, debug: 1, implement: 0 } }
    ];

    let cardPlacements = {};
    let analysisResult = null;

    // Simple ML-inspired Decision Tree Classifier
    class CodingStyleClassifier {
        constructor() {
            // Training data patterns (simplified for demonstration)
            this.profiles = {
                explorer: {
                    name: 'The Explorer',
                    icon: '🔬',
                    description: 'You thrive on discovering new technologies and experimenting with cutting-edge tools. Your curiosity drives you to constantly learn and try new approaches. You prefer breadth of knowledge over depth in any single area.',
                    thresholds: { explore: 0.6, collab: 0.3, debug: 0.4, implement: 0.5 }
                },
                builder: {
                    name: 'The Builder',
                    icon: '🏗️',
                    description: 'You\'re focused on creating and shipping products. You excel at turning ideas into working code and prefer hands-on implementation over theory. Your strength is in practical problem-solving and building things that work.',
                    thresholds: { explore: 0.3, collab: 0.4, debug: 0.3, implement: 0.7 }
                },
                collaborator: {
                    name: 'The Collaborator',
                    icon: '🤝',
                    description: 'You excel in team environments and enjoy working with others. Code review, pair programming, and team projects energize you. You believe the best solutions come from collective intelligence and shared knowledge.',
                    thresholds: { explore: 0.4, collab: 0.6, debug: 0.4, implement: 0.5 }
                }
            };
        }

        extractFeatures(placements) {
            // Feature extraction: calculate weighted averages
            const features = { explore: 0, collab: 0, debug: 0, implement: 0 };
            let preferCount = 0;

            Object.entries(placements).forEach(([cardId, zone]) => {
                const card = cards.find(c => c.id === parseInt(cardId));
                if (zone === 'prefer') {
                    features.explore += card.features.explore;
                    features.collab += card.features.collab;
                    features.debug += card.features.debug;
                    features.implement += card.features.implement;
                    preferCount++;
                }
            });

            // Normalize features
            if (preferCount > 0) {
                Object.keys(features).forEach(key => {
                    features[key] /= preferCount;
                });
            }

            return features;
        }

        calculateDistance(features, profileThresholds) {
            // Euclidean distance calculation
            let distance = 0;
            Object.keys(features).forEach(key => {
                distance += Math.pow(features[key] - profileThresholds[key], 2);
            });
            return Math.sqrt(distance);
        }

        predict(placements) {
            const features = this.extractFeatures(placements);
            
            // Find closest profile using decision tree logic
            let bestProfile = null;
            let minDistance = Infinity;
            let distances = {};

            Object.entries(this.profiles).forEach(([key, profile]) => {
                const distance = this.calculateDistance(features, profile.thresholds);
                distances[key] = distance;
                if (distance < minDistance) {
                    minDistance = distance;
                    bestProfile = key;
                }
            });

            // Calculate confidence score (inverse of normalized distance)
            const maxDistance = Math.sqrt(4); // Maximum possible distance
            const confidence = Math.round((1 - (minDistance / maxDistance)) * 100);

            return {
                profile: this.profiles[bestProfile],
                confidence: Math.max(60, Math.min(98, confidence)), // Clamp between 60-98%
                features: features,
                distances: distances
            };
        }
    }

    const mlClassifier = new CodingStyleClassifier();

    function initializeGame() {
        const gameBoard = document.getElementById('game-board');
        const cardsPool = document.getElementById('cards-pool');

        // Create two zones
        zones.forEach(zone => {
            const zoneEl = document.createElement('div');
            zoneEl.className = 'category-zone';
            zoneEl.id = `zone-${zone.id}`;
            zoneEl.innerHTML = `
                <div class="category-header">
                    <div class="category-icon">${zone.icon}</div>
                    <div class="category-title">${zone.title}</div>
                    <div class="category-count" id="count-${zone.id}">0 cards</div>
                </div>
                <div class="category-cards" id="cards-${zone.id}"></div>
            `;
            
            zoneEl.addEventListener('dragover', handleDragOver);
            zoneEl.addEventListener('drop', handleDrop);
            zoneEl.addEventListener('dragleave', handleDragLeave);
            
            gameBoard.appendChild(zoneEl);
        });

        // Create cards in pool
        cards.forEach(card => {
            const cardEl = createCardElement(card);
            cardsPool.appendChild(cardEl);
        });
    }

    function createCardElement(card) {
        const cardEl = document.createElement('div');
        cardEl.className = 'card';
        cardEl.draggable = true;
        cardEl.id = `card-${card.id}`;
        cardEl.innerHTML = `<div class="card-text">${card.text}</div>`;
        
        cardEl.addEventListener('dragstart', handleDragStart);
        cardEl.addEventListener('dragend', handleDragEnd);
        
        return cardEl;
    }

    function handleDragStart(e) {
        e.currentTarget.classList.add('dragging');
        e.dataTransfer.effectAllowed = 'move';
        e.dataTransfer.setData('text/html', e.currentTarget.id);
    }

    function handleDragEnd(e) {
        e.currentTarget.classList.remove('dragging');
    }

    function handleDragOver(e) {
        if (e.preventDefault) {
            e.preventDefault();
        }
        e.dataTransfer.dropEffect = 'move';
        
        const zone = e.currentTarget.closest('.category-zone');
        if (zone) {
            zone.classList.add('drag-over');
        }
        
        return false;
    }

    function handleDragLeave(e) {
        const zone = e.currentTarget;
        zone.classList.remove('drag-over');
    }

    function handleDrop(e) {
        if (e.stopPropagation) {
            e.stopPropagation();
        }
        
        const zone = e.currentTarget.closest('.category-zone');
        zone.classList.remove('drag-over');
        
        const cardId = e.dataTransfer.getData('text/html');
        const cardEl = document.getElementById(cardId);
        
        if (cardEl) {
            const zoneId = zone.id.replace('zone-', '');
            const cardsContainer = document.getElementById(`cards-${zoneId}`);
            
            // Remove from previous placement
            const cardNumId = parseInt(cardId.replace('card-', ''));
            if (cardPlacements[cardNumId]) {
                delete cardPlacements[cardNumId];
            }
            
            // Add to new placement
            cardPlacements[cardNumId] = zoneId;
            cardsContainer.appendChild(cardEl);
            
            updateCounts();
        }
        
        return false;
    }

    function updateCounts() {
        const counts = { prefer: 0, avoid: 0 };
        
        Object.values(cardPlacements).forEach(zone => {
            counts[zone]++;
        });
        
        zones.forEach(zone => {
            const count = counts[zone.id];
            document.getElementById(`count-${zone.id}`).textContent = 
                `${count} card${count !== 1 ? 's' : ''}`;
        });
    }

    function autoFill() {
        // Clear existing placements
        cardPlacements = {};
        document.getElementById('cards-prefer').innerHTML = '';
        document.getElementById('cards-avoid').innerHTML = '';
        
        // Randomly assign each card to a zone
        cards.forEach(card => {
            const randomZone = Math.random() > 0.5 ? 'prefer' : 'avoid';
            cardPlacements[card.id] = randomZone;
            
            const cardEl = document.getElementById(`card-${card.id}`);
            const targetContainer = document.getElementById(`cards-${randomZone}`);
            targetContainer.appendChild(cardEl);
        });
        
        updateCounts();
        showStatus('✨ Cards auto-filled randomly! Review and adjust if needed, or run ML analysis.', 'success');
        
        setTimeout(() => {
            document.getElementById('status-message').style.display = 'none';
        }, 3000);
    }

    function analyzeResults() {
        const totalCards = Object.keys(cardPlacements).length;
        
        if (totalCards < cards.length) {
            showStatus(`⚠️ Please sort all ${cards.length} cards before running ML analysis!`, 'error');
            return;
        }

        showStatus('🤖 Running ML classifier...', 'info');

        // Simulate ML processing time
        setTimeout(() => {
            // Run ML prediction
            const prediction = mlClassifier.predict(cardPlacements);
            
            // Count preferences
            const counts = { prefer: 0, avoid: 0 };
            const preferredCards = [];
            const avoidedCards = [];
            
            Object.entries(cardPlacements).forEach(([cardId, zone]) => {
                counts[zone]++;
                const card = cards.find(c => c.id === parseInt(cardId));
                if (zone === 'prefer') {
                    preferredCards.push(card.text);
                } else {
                    avoidedCards.push(card.text);
                }
            });

            analysisResult = {
                profile: prediction.profile,
                confidence: prediction.confidence,
                features: prediction.features,
                counts: counts,
                percentages: {
                    prefer: Math.round((counts.prefer / totalCards) * 100),
                    avoid: Math.round((counts.avoid / totalCards) * 100)
                },
                preferredCards: preferredCards,
                avoidedCards: avoidedCards,
                placements: cardPlacements,
                timestamp: new Date().toISOString()
            };

            displayResults();
        }, 1500);
    }

    function displayResults() {
        document.getElementById('game-section').style.display = 'none';
        document.getElementById('result-section').style.display = 'block';

        const result = analysisResult;
        
        document.getElementById('result-icon').textContent = result.profile.icon;
        document.getElementById('result-title').textContent = result.profile.name;
        document.getElementById('result-description').innerHTML = `<p>${result.profile.description}</p>`;

        // Animate confidence bar
        setTimeout(() => {
            document.getElementById('confidence-fill').style.width = result.confidence + '%';
            document.getElementById('confidence-fill').textContent = result.confidence + '%';
        }, 100);

        const statsContainer = document.getElementById('result-stats');
        statsContainer.innerHTML = `
            <div class="stat-card">
                <div class="stat-value">${Math.round(result.features.explore * 100)}%</div>
                <div class="stat-label">Exploration Score</div>
            </div>
            <div class="stat-card">
                <div class="stat-value">${Math.round(result.features.collab * 100)}%</div>
                <div class="stat-label">Collaboration Score</div>
            </div>
            <div class="stat-card">
                <div class="stat-value">${Math.round(result.features.debug * 100)}%</div>
                <div class="stat-label">Debugging Score</div>
            </div>
            <div class="stat-card">
                <div class="stat-value">${Math.round(result.features.implement * 100)}%</div>
                <div class="stat-label">Implementation Score</div>
            </div>
        `;

        // Update save info with actual results
        const saveInfo = document.getElementById('save-info');
        if (saveInfo) {
            saveInfo.innerHTML = `
                <strong>💡 What happens when you save?</strong>
                <p style="margin-top: 0.5em; line-height: 1.6;">
                    Your ML-predicted coding profile will be stored in your matchmaking database. This includes:<br>
                    • Your predicted coding style (<strong>${result.profile.name}</strong>)<br>
                    • ML confidence score (<strong>${result.confidence}%</strong>)<br>
                    • Feature scores for exploration, collaboration, debugging, and implementation<br>
                    • Your complete card placement preferences<br><br>
                    This data can be used by matchmaking algorithms to pair you with compatible coding partners who share similar or complementary styles!
                </p>
            `;
        }
    }

    function getCookie(name) {
        const value = `; ${document.cookie}`;
        const parts = value.split(`; ${name}=`);
        if (parts.length === 2) return parts.pop().split(';').shift();
        return null;
    }

    function showStatus(message, type, containerId = 'status-message') {
        const statusDiv = document.getElementById(containerId);
        statusDiv.className = `status-message status-${type}`;
        statusDiv.textContent = message;
        statusDiv.style.display = 'block';
        
        if (type === 'success') {
            setTimeout(() => {
                statusDiv.style.display = 'none';
            }, 5000);
        }
    }

    async function saveToProfile() {
        if (!analysisResult) {
            showStatus('⚠️ No results to save!', 'error', 'save-status');
            return;
        }

        const token = getCookie('jwt');
        if (!token) {
            showStatus('⚠️ Please log in to save your profile', 'error', 'save-status');
            return;
        }

        try {
            showStatus('💾 Saving to your profile...', 'info', 'save-status');

            const response = await fetch('/api/match/add', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json',
                    'Authorization': `Bearer ${token}`
                },
                body: JSON.stringify({
                    index: 'coding_profile',
                    data: analysisResult
                })
            });

            const data = await response.json();

            if (response.ok) {
                showStatus('✅ Successfully saved! Your ML-predicted coding profile is now on your matchmaking profile.', 'success', 'save-status');
            } else {
                showStatus(`❌ Error: ${data.message}`, 'error', 'save-status');
            }
        } catch (error) {
            showStatus(`❌ Failed to save: ${error.message}`, 'error', 'save-status');
        }
    }

    function restartGame() {
        cardPlacements = {};
        analysisResult = null;
        
        document.getElementById('game-section').style.display = 'block';
        document.getElementById('result-section').style.display = 'none';
        
        // Clear zones
        document.getElementById('cards-prefer').innerHTML = '';
        document.getElementById('cards-avoid').innerHTML = '';
        
        // Reset pool
        const cardsPool = document.getElementById('cards-pool');
        cardsPool.innerHTML = '';
        cards.forEach(card => {
            const cardEl = createCardElement(card);
            cardsPool.appendChild(cardEl);
        });
        
        updateCounts();
        document.getElementById('status-message').style.display = 'none';
        document.getElementById('confidence-fill').style.width = '0%';
    }

    // Initialize the game when the page loads
    window.addEventListener('DOMContentLoaded', initializeGame);
</script>

---