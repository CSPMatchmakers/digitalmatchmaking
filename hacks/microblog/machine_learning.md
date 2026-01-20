---
layout: post
title: Machine Learning with Titanic
description: Understanding Machine Learning concepts through interactive Titanic survival prediction.
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

    .ml-container {
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

    .ml-container h1 {
        text-align: center;
        color: #8b9dff;
        font-size: 2.5em;
        margin-bottom: 0.3em;
        text-shadow: 0 0 20px rgba(139, 157, 255, 0.5);
    }

    .subtitle {
        text-align: center;
        color: #c0c0c0;
        margin-bottom: 2em;
        font-size: 1.1em;
    }

    .info-box {
        background: linear-gradient(135deg, #2a2a40 0%, #1f1f35 100%);
        padding: 1.5em;
        border-radius: 12px;
        margin-bottom: 2em;
        border-left: 4px solid #667eea;
        box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
    }

    .info-box h2 {
        color: #8b9dff;
        margin-bottom: 0.8em;
        font-size: 1.5em;
    }

    .info-box p {
        line-height: 1.8;
        color: #c0c0c0;
        margin-bottom: 0.8em;
    }

    .info-box ul {
        margin-left: 1.5em;
        color: #c0c0c0;
        line-height: 1.8;
    }

    .info-box strong {
        color: #8b9dff;
    }

    .tabs {
        display: flex;
        gap: 1em;
        margin-bottom: 2em;
        flex-wrap: wrap;
    }

    .tab-btn {
        flex: 1;
        min-width: 150px;
        padding: 1em;
        background: #2a2a40;
        color: #8b9dff;
        border: 2px solid #667eea;
        border-radius: 8px;
        cursor: pointer;
        font-weight: bold;
        font-size: 1em;
        transition: all 0.3s;
        font-family: 'Courier New', monospace;
    }

    .tab-btn:hover {
        background: #3a3a52;
        transform: translateY(-2px);
        box-shadow: 0 4px 12px rgba(102, 126, 234, 0.3);
    }

    .tab-btn.active {
        background: #667eea;
        color: white;
    }

    .tab-content {
        display: none;
        animation: fadeIn 0.3s ease-in;
    }

    .tab-content.active {
        display: block;
    }

    @keyframes fadeIn {
        from { opacity: 0; }
        to { opacity: 1; }
    }

    .predictor-panel {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 2em;
        margin-bottom: 2em;
    }

    @media (max-width: 768px) {
        .predictor-panel {
            grid-template-columns: 1fr;
        }
    }

    .input-section {
        background: #2a2a40;
        padding: 1.5em;
        border-radius: 12px;
        border: 2px solid #667eea;
    }

    .form-group {
        margin-bottom: 1.5em;
    }

    .form-group label {
        display: block;
        color: #8b9dff;
        font-weight: bold;
        margin-bottom: 0.5em;
    }

    .form-group select,
    .form-group input {
        width: 100%;
        padding: 0.8em;
        background: #1f1f35;
        border: 2px solid #667eea;
        border-radius: 8px;
        color: #e0e0e0;
        font-size: 1em;
        transition: all 0.3s;
        font-family: 'Courier New', monospace;
    }

    .form-group select:focus,
    .form-group input:focus {
        outline: none;
        border-color: #8b9dff;
        box-shadow: 0 0 12px rgba(139, 157, 255, 0.3);
    }

    .predict-btn {
        width: 100%;
        padding: 1em;
        background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
        color: white;
        border: none;
        border-radius: 8px;
        font-size: 1.1em;
        font-weight: bold;
        cursor: pointer;
        transition: all 0.3s;
        font-family: 'Courier New', monospace;
    }

    .predict-btn:hover {
        transform: translateY(-2px);
        box-shadow: 0 8px 20px rgba(102, 126, 234, 0.4);
    }

    .result-section {
        background: #2a2a40;
        padding: 1.5em;
        border-radius: 12px;
        border: 2px solid #667eea;
        text-align: center;
    }

    .result-icon {
        font-size: 4em;
        margin-bottom: 0.3em;
    }

    .result-text {
        font-size: 1.5em;
        font-weight: bold;
        margin-bottom: 0.5em;
    }

    .survived {
        color: #27ae60;
    }

    .not-survived {
        color: #e74c3c;
    }

    .probability {
        font-size: 1.1em;
        color: #8b9dff;
        margin-bottom: 1em;
    }

    .explanation {
        background: #1f1f35;
        padding: 1em;
        border-radius: 8px;
        text-align: left;
        color: #c0c0c0;
        line-height: 1.6;
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

    .quiz-question {
        background: #2a2a40;
        padding: 1.5em;
        border-radius: 12px;
        border: 2px solid #667eea;
        margin-bottom: 1.5em;
    }

    .quiz-question h3 {
        color: #8b9dff;
        margin-bottom: 1em;
        font-size: 1.4em;
    }

    .quiz-option {
        background: #1f1f35;
        padding: 1.2em 1.5em;
        margin: 0.8em 0;
        border-radius: 8px;
        border: 2px solid #667eea;
        cursor: pointer;
        transition: all 0.3s;
        font-size: 1.05em;
    }

    .quiz-option:hover {
        background: #2a2a40;
        border-color: #8b9dff;
    }

    .quiz-option.correct {
        background: #27ae60;
        border-color: #27ae60;
        color: white;
    }

    .quiz-option.incorrect {
        background: #e74c3c;
        border-color: #e74c3c;
        color: white;
    }

    .data-table {
        width: 100%;
        background: #2a2a40;
        border-radius: 12px;
        overflow: hidden;
        border: 2px solid #667eea;
    }

    .data-table th {
        background: #667eea;
        color: white;
        padding: 1em;
        text-align: left;
    }

    .data-table td {
        padding: 1em;
        border-bottom: 1px solid #3a3a52;
    }

    .data-table tr:hover {
        background: #3a3a52;
    }

    .progress-bar {
        width: 100%;
        height: 40px;
        background: #1f1f35;
        border-radius: 15px;
        overflow: hidden;
        margin: 1em 0;
    }

    .progress-fill {
        height: 100%;
        background: linear-gradient(90deg, #667eea, #764ba2);
        transition: width 0.5s ease;
        display: flex;
        align-items: center;
        justify-content: center;
        color: white;
        font-weight: bold;
        font-size: 1.1em;
    }
</style>



<div class="ml-container">
    <h1>🚢 Titanic ML Explorer</h1>
    <p class="subtitle">Interactive Machine Learning with the Titanic Dataset</p>

    <div class="tabs">
        <button class="tab-btn active" onclick="switchTab('personality')">🧠 Personality Quiz</button>
        <button class="tab-btn" onclick="switchTab('learn')">📚 Learn</button>
        <button class="tab-btn" onclick="switchTab('predict')">🔮 Predict</button>
        <button class="tab-btn" onclick="switchTab('quiz')">🎯 Quiz</button>
    </div>

    <!-- Personality Quiz Tab (Now First) -->
    <div id="personality-tab" class="tab-content active">
        <div class="info-box">
            <h2>🧠 Discover Your Coder Personality</h2>
            <p>Take this quiz to find out what type of coder you are! Your result will be saved to your profile for matchmaking.</p>
        </div>

        <div id="personality-status-container"></div>

        <div id="personality-quiz-section">
            <div class="progress-bar" style="margin-bottom: 2em;">
                <div class="progress-fill" id="personality-progress" style="width: 0%">0%</div>
            </div>

            <div id="personality-question-container"></div>

            <div style="text-align: center; margin-top: 2em;">
                <button class="predict-btn" id="personality-next-btn" onclick="nextPersonalityQuestion()" disabled>
                    Next Question →
                </button>
            </div>
        </div>

        <div id="personality-result-section" style="display: none;">
            <div style="text-align: center;">
                <div style="font-size: 5em; margin-bottom: 0.3em;" id="personality-result-icon">🎯</div>
                <div style="font-size: 2.5em; color: #8b9dff; font-weight: bold; margin-bottom: 0.5em;" id="personality-result-name">Your Coder Type</div>
                <div class="info-box" id="personality-result-description"></div>
                
                <div class="stats-grid" id="personality-traits-container"></div>

                <div style="margin-top: 2em;">
                    <button class="predict-btn" onclick="savePersonalityToProfile()">
                        💾 Save to Profile
                    </button>
                    <button class="predict-btn" onclick="restartPersonalityQuiz()">
                        🔄 Retake Quiz
                    </button>
                </div>
            </div>
        </div>
    </div>

    <!-- Learn Tab -->
    <div id="learn-tab" class="tab-content active">
        <div class="info-box">
            <h2>📖 Understanding the Titanic ML Model</h2>
            <p>The Titanic disaster of 1912 is one of the most infamous shipwrecks in history. Out of 2,224 passengers and crew aboard, only 722 survived. Machine learning helps us understand what factors influenced survival.</p>
        </div>

        <h2 style="color: #8b9dff; margin-bottom: 1em;">Key Factors Affecting Survival</h2>
        <div class="stats-grid">
            <div class="stat-card">
                <div class="stat-value">74%</div>
                <div class="stat-label">Women survived</div>
            </div>
            <div class="stat-card">
                <div class="stat-value">19%</div>
                <div class="stat-label">Men survived</div>
            </div>
            <div class="stat-card">
                <div class="stat-value">63%</div>
                <div class="stat-label">1st Class survived</div>
            </div>
            <div class="stat-card">
                <div class="stat-value">24%</div>
                <div class="stat-label">3rd Class survived</div>
            </div>
        </div>

        <div class="info-box">
            <h2>🔍 How the ML Model Works</h2>
            <p><strong>Step 1: Data Collection</strong><br>We gather information about each passenger (age, gender, ticket class, etc.)</p>
            <p><strong>Step 2: Feature Engineering</strong><br>We convert text data (like "male"/"female") into numbers the computer can understand</p>
            <p><strong>Step 3: Training</strong><br>The model learns patterns from passengers we know survived or didn't survive</p>
            <p><strong>Step 4: Prediction</strong><br>The model can now predict survival for new passengers based on learned patterns</p>
        </div>
    </div>

    <!-- Predict Tab -->
    <div id="predict-tab" class="tab-content">
        <div class="info-box">
            <h2>🔮 Make Your Prediction</h2>
            <p>Enter passenger information below and see if our ML model predicts they would have survived the Titanic disaster!</p>
        </div>

        <div class="predictor-panel">
            <div class="input-section">
                <h3 style="color: #8b9dff; margin-bottom: 1em;">Passenger Information</h3>
                
                <div class="form-group">
                    <label>Passenger Class</label>
                    <select id="pclass">
                        <option value="1">1st Class (Upper deck)</option>
                        <option value="2">2nd Class (Middle deck)</option>
                        <option value="3" selected>3rd Class (Lower deck)</option>
                    </select>
                </div>

                <div class="form-group">
                    <label>Sex</label>
                    <select id="sex">
                        <option value="male">Male</option>
                        <option value="female">Female</option>
                    </select>
                </div>

                <div class="form-group">
                    <label>Age</label>
                    <input type="number" id="age" value="30" min="0" max="100">
                </div>

                <div class="form-group">
                    <label>Number of Siblings/Spouses Aboard</label>
                    <input type="number" id="sibsp" value="0" min="0" max="10">
                </div>

                <div class="form-group">
                    <label>Number of Parents/Children Aboard</label>
                    <input type="number" id="parch" value="0" min="0" max="10">
                </div>

                <div class="form-group">
                    <label>Fare Paid (£)</label>
                    <input type="number" id="fare" value="15" min="0" step="0.01">
                </div>

                <button class="predict-btn" onclick="makePrediction()">🔮 Predict Survival</button>
            </div>

            <div class="result-section" id="result-section">
                <div style="padding: 2em;">
                    <div style="font-size: 3em; margin-bottom: 0.5em;">🤔</div>
                    <p style="color: #8b9dff; font-size: 1.2em;">Enter passenger details and click "Predict Survival" to see the result!</p>
                </div>
            </div>
        </div>
    </div>

    <!-- Explore Data Tab -->
    <div id="explore-tab" class="tab-content">
        <div class="info-box">
            <h2>📊 Dataset Overview</h2>
            <p>The Titanic dataset contains information about 891 passengers. Here are some sample records:</p>
        </div>

        <div style="overflow-x: auto;">
            <table class="data-table">
                <thead>
                    <tr>
                        <th>Name</th>
                        <th>Age</th>
                        <th>Sex</th>
                        <th>Class</th>
                        <th>Fare</th>
                        <th>Survived</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>Braund, Mr. Owen Harris</td>
                        <td>22</td>
                        <td>male</td>
                        <td>3rd</td>
                        <td>£7.25</td>
                        <td>❌ No</td>
                    </tr>
                    <tr>
                        <td>Cumings, Mrs. John Bradley</td>
                        <td>38</td>
                        <td>female</td>
                        <td>1st</td>
                        <td>£71.28</td>
                        <td>✅ Yes</td>
                    </tr>
                    <tr>
                        <td>Heikkinen, Miss. Laina</td>
                        <td>26</td>
                        <td>female</td>
                        <td>3rd</td>
                        <td>£7.92</td>
                        <td>✅ Yes</td>
                    </tr>
                    <tr>
                        <td>Futrelle, Mrs. Jacques Heath</td>
                        <td>35</td>
                        <td>female</td>
                        <td>1st</td>
                        <td>£53.10</td>
                        <td>✅ Yes</td>
                    </tr>
                    <tr>
                        <td>Allen, Mr. William Henry</td>
                        <td>35</td>
                        <td>male</td>
                        <td>3rd</td>
                        <td>£8.05</td>
                        <td>❌ No</td>
                    </tr>
                </tbody>
            </table>
        </div>

        <div class="info-box" style="margin-top: 2em;">
            <h2>📈 Key Insights</h2>
            <p><strong>Gender was the strongest predictor:</strong> Women had a much higher survival rate (74%) compared to men (19%). This reflects the "women and children first" evacuation policy.</p>
            <p><strong>Class mattered:</strong> First-class passengers had better access to lifeboats and survived at higher rates (63%) than third-class passengers (24%).</p>
            <p><strong>Age played a role:</strong> Children had higher survival rates, as they were prioritized during evacuation.</p>
            <p><strong>Family size:</strong> Having some family members improved survival chances, but very large families had lower survival rates.</p>
        </div>
    </div>

    <!-- Quiz Tab -->
    <div id="quiz-tab" class="tab-content">
        <div class="info-box">
            <h2>🎯 Test Your Knowledge</h2>
            <p>Answer these questions to test your understanding of machine learning and the Titanic dataset!</p>
        </div>

        <div class="quiz-question" id="q1">
            <h3>Question 1: What is a "feature" in machine learning?</h3>
            <div class="quiz-option" onclick="checkAnswer(1, 'a')">A) The final prediction</div>
            <div class="quiz-option" onclick="checkAnswer(1, 'b')">B) Input variables used to make predictions</div>
            <div class="quiz-option" onclick="checkAnswer(1, 'c')">C) The training dataset</div>
            <div class="quiz-option" onclick="checkAnswer(1, 'd')">D) The computer algorithm</div>
            <div id="q1-feedback" style="margin-top: 1em; display: none;"></div>
        </div>

        <div class="quiz-question" id="q2">
            <h3>Question 2: Which group had the highest survival rate on the Titanic?</h3>
            <div class="quiz-option" onclick="checkAnswer(2, 'a')">A) Men in 1st class</div>
            <div class="quiz-option" onclick="checkAnswer(2, 'b')">B) Women in 3rd class</div>
            <div class="quiz-option" onclick="checkAnswer(2, 'c')">C) Women in 1st class</div>
            <div class="quiz-option" onclick="checkAnswer(2, 'd')">D) Children in 3rd class</div>
            <div id="q2-feedback" style="margin-top: 1em; display: none;"></div>
        </div>

        <div class="quiz-question" id="q3">
            <h3>Question 3: What type of ML problem is Titanic survival prediction?</h3>
            <div class="quiz-option" onclick="checkAnswer(3, 'a')">A) Regression (predicting a number)</div>
            <div class="quiz-option" onclick="checkAnswer(3, 'b')">B) Classification (predicting a category)</div>
            <div class="quiz-option" onclick="checkAnswer(3, 'c')">C) Clustering (grouping similar items)</div>
            <div class="quiz-option" onclick="checkAnswer(3, 'd')">D) Reinforcement learning</div>
            <div id="q3-feedback" style="margin-top: 1em; display: none;"></div>
        </div>

        <div id="quiz-score" style="display: none; text-align: center; padding: 2em;">
            <h2 style="color: #8b9dff;">Quiz Complete!</h2>
            <div class="stat-value" id="score-display">0/3</div>
            <p style="color: #c0c0c0; margin-top: 1em;">Great job learning about ML and the Titanic dataset!</p>
        </div>
    </div>

    <!-- Personality Quiz Tab -->
    <div id="personality-tab" class="tab-content">
        <div class="info-box">
            <h2>🧠 Discover Your Coder Personality</h2>
            <p>Take this quiz to find out what type of coder you are! Your result will be saved to your profile for matchmaking.</p>
        </div>

        <div id="personality-status-container"></div>

        <div id="personality-quiz-section">
            <div class="progress-bar" style="margin-bottom: 2em;">
                <div class="progress-fill" id="personality-progress" style="width: 0%">0%</div>
            </div>

            <div id="personality-question-container"></div>

            <div style="text-align: center; margin-top: 2em;">
                <button class="predict-btn" id="personality-next-btn" onclick="nextPersonalityQuestion()" disabled>
                    Next Question →
                </button>
            </div>
        </div>

        <div id="personality-result-section" style="display: none;">
            <div style="text-align: center;">
                <div style="font-size: 5em; margin-bottom: 0.3em;" id="personality-result-icon">🎯</div>
                <div style="font-size: 2.5em; color: #8b9dff; font-weight: bold; margin-bottom: 0.5em;" id="personality-result-name">Your Coder Type</div>
                <div class="info-box" id="personality-result-description"></div>
                
                <div class="stats-grid" id="personality-traits-container"></div>

                <div style="margin-top: 2em;">
                    <button class="predict-btn" onclick="savePersonalityToProfile()">
                        💾 Save to Profile
                    </button>
                    <button class="predict-btn" onclick="restartPersonalityQuiz()">
                        🔄 Retake Quiz
                    </button>
                </div>
            </div>
        </div>
    </div>
</div>

<script>
    // LISTS (AP CSP Requirement: Collection Type)
    let quizAnswers = {1: 'b', 2: 'c', 3: 'b'};
    let userAnswers = {};
    let quizComplete = false;

    function switchTab(tab) {
        const tabs = ['personality', 'learn', 'predict', 'explore', 'quiz'];
        for (let i = 0; i < tabs.length; i++) {
            const tabEl = document.getElementById(tabs[i] + '-tab');
            if (tabEl) tabEl.classList.remove('active');
        }
        const activeTab = document.getElementById(tab + '-tab');
        if (activeTab) activeTab.classList.add('active');
        
        const buttons = document.querySelectorAll('.tab-btn');
        const tabNames = ['personality', 'learn', 'predict', 'explore', 'quiz'];
        for (let i = 0; i < buttons.length; i++) {
            buttons[i].classList.remove('active');
            if (tabNames[i] === tab) buttons[i].classList.add('active');
        }
    }

    function calculateSurvivalScore(passenger) {
        let score = 50;
        if (passenger.sex === 'female') score += 30;
        else score -= 25;
        if (passenger.pclass === 1) score += 15;
        else if (passenger.pclass === 3) score -= 15;
        if (passenger.age < 16) score += 10;
        else if (passenger.age > 60) score -= 10;
        const familySize = passenger.sibsp + passenger.parch;
        if (familySize >= 1 && familySize <= 3) score += 5;
        else if (familySize > 4) score -= 10;
        if (passenger.fare > 50) score += 10;
        else if (passenger.fare < 10) score -= 5;
        return Math.max(0, Math.min(100, score));
    }

    function makePrediction() {
        const passenger = {
            pclass: parseInt(document.getElementById('pclass').value),
            sex: document.getElementById('sex').value,
            age: parseFloat(document.getElementById('age').value),
            sibsp: parseInt(document.getElementById('sibsp').value),
            parch: parseInt(document.getElementById('parch').value),
            fare: parseFloat(document.getElementById('fare').value)
        };
        const survivalScore = calculateSurvivalScore(passenger);
        const survived = survivalScore >= 50;
        const familySize = passenger.sibsp + passenger.parch;
        displayResult(survived, survivalScore, {
            pclass: passenger.pclass, sex: passenger.sex, 
            age: passenger.age, familySize: familySize
        });
    }

    function displayResult(survived, probability, factors) {
        const resultSection = document.getElementById('result-section');
        const icon = survived ? '✅' : '❌';
        const resultClass = survived ? 'survived' : 'not-survived';
        const resultText = survived ? 'LIKELY SURVIVED' : 'LIKELY NOT SURVIVED';
        let explanation = survived ? 
            'Based on the model, this passenger likely survived because ' :
            'Based on the model, this passenger likely did not survive because ';
        const reasons = [];
        if (factors.sex === 'female') reasons.push('they were female (women had priority in lifeboats)');
        else reasons.push('they were male (men had lower priority)');
        if (factors.pclass === 1) reasons.push('they were in 1st class (better lifeboat access)');
        else if (factors.pclass === 3) reasons.push('they were in 3rd class (limited lifeboat access)');
        if (factors.age < 16) reasons.push('they were a child (children were prioritized)');
        if (factors.familySize > 0 && factors.familySize <= 3) {
            reasons.push('they had family aboard (small families helped each other)');
        }
        explanation += reasons.join(', ') + '.';
        resultSection.innerHTML = `
            <div class="result-icon">${icon}</div>
            <div class="result-text ${resultClass}">${resultText}</div>
            <div class="probability">Survival Probability: ${probability}%</div>
            <div class="progress-bar">
                <div class="progress-fill" style="width: ${probability}%">${probability}%</div>
            </div>
            <div class="explanation">
                <strong>Explanation:</strong><br>${explanation}
            </div>
        `;
    }

    function checkAnswer(questionNum, answer) {
        if (quizComplete) return;
        const correct = quizAnswers[questionNum] === answer;
        const options = document.querySelectorAll('#q' + questionNum + ' .quiz-option');
        const feedback = document.getElementById('q' + questionNum + '-feedback');
        for (let i = 0; i < options.length; i++) {
            const opt = options[i];
            opt.style.pointerEvents = 'none';
            if (opt.textContent.includes(answer.toUpperCase() + ')')) {
                opt.classList.add(correct ? 'correct' : 'incorrect');
            }
            if (opt.textContent.includes(quizAnswers[questionNum].toUpperCase() + ')')) {
                opt.classList.add('correct');
            }
        }
        userAnswers[questionNum] = correct;
        if (correct) {
            feedback.innerHTML = '<div style="color: #27ae60;">✅ Correct! Great job!</div>';
        } else {
            feedback.innerHTML = '<div style="color: #e74c3c;">❌ Not quite. The correct answer is highlighted in green.</div>';
        }
        feedback.style.display = 'block';
        if (Object.keys(userAnswers).length === 3) showQuizScore();
    }

    function showQuizScore() {
        quizComplete = true;
        let correctCount = 0;
        const answerKeys = Object.keys(userAnswers);
        for (let i = 0; i < answerKeys.length; i++) {
            if (userAnswers[answerKeys[i]]) correctCount++;
        }
        document.getElementById('quiz-score').style.display = 'block';
        document.getElementById('score-display').textContent = correctCount + '/3';
    }

    // Personality Quiz Section

    const personalityQuestions = [
        {
            question: "When faced with a complex coding problem, what's your first move?",
            options: [
                { text: "Break it down into smaller pieces and tackle them one by one", weights: { architect: 3, debugger: 2, innovator: 1 } },
                { text: "Search for existing solutions and adapt them", weights: { pragmatist: 3, hacker: 2, learner: 1 } },
                { text: "Experiment with different approaches until something works", weights: { innovator: 3, hacker: 2, artist: 1 } },
                { text: "Plan the entire solution before writing any code", weights: { architect: 3, perfectionist: 2, debugger: 1 } }
            ]
        },
        {
            question: "How do you feel about code documentation?",
            options: [
                { text: "It's essential! Every function needs detailed comments", weights: { architect: 3, perfectionist: 2, learner: 1 } },
                { text: "Code should be self-explanatory, minimal docs needed", weights: { artist: 3, pragmatist: 2, hacker: 1 } },
                { text: "I document the tricky parts, skip the obvious stuff", weights: { pragmatist: 3, debugger: 2, innovator: 1 } },
                { text: "What's documentation? The code IS the documentation", weights: { hacker: 3, innovator: 2, artist: 1 } }
            ]
        },
        {
            question: "Your code works perfectly. What do you do next?",
            options: [
                { text: "Refactor it to make it cleaner and more efficient", weights: { perfectionist: 3, architect: 2, artist: 1 } },
                { text: "Ship it! If it works, don't touch it", weights: { pragmatist: 3, hacker: 2, debugger: 1 } },
                { text: "Add extra features I thought of while coding", weights: { innovator: 3, artist: 2, learner: 1 } },
                { text: "Write tests to make sure it keeps working", weights: { architect: 3, debugger: 2, perfectionist: 1 } }
            ]
        },
        {
            question: "What's your relationship with debugging?",
            options: [
                { text: "I love it! Finding bugs is like solving puzzles", weights: { debugger: 3, perfectionist: 2, architect: 1 } },
                { text: "Necessary evil. Console.log() is my best friend", weights: { pragmatist: 3, hacker: 2, learner: 1 } },
                { text: "Frustrating. I'd rather rewrite than debug", weights: { innovator: 3, artist: 2, hacker: 1 } },
                { text: "Strategic. I use proper debugging tools and techniques", weights: { architect: 3, debugger: 2, perfectionist: 1 } }
            ]
        },
        {
            question: "How do you learn new technologies?",
            options: [
                { text: "Read the entire documentation first", weights: { learner: 3, architect: 2, perfectionist: 1 } },
                { text: "Jump straight into coding and learn by doing", weights: { hacker: 3, innovator: 2, pragmatist: 1 } },
                { text: "Follow tutorials and adapt them to my needs", weights: { learner: 3, pragmatist: 2, debugger: 1 } },
                { text: "Build something creative to explore capabilities", weights: { artist: 3, innovator: 2, learner: 1 } }
            ]
        },
        {
            question: "What motivates you most when coding?",
            options: [
                { text: "Creating something beautiful and elegant", weights: { artist: 3, perfectionist: 2, architect: 1 } },
                { text: "Solving real-world problems efficiently", weights: { pragmatist: 3, architect: 2, debugger: 1 } },
                { text: "Learning and mastering new skills", weights: { learner: 3, debugger: 2, innovator: 1 } },
                { text: "Building something innovative and unique", weights: { innovator: 3, artist: 2, hacker: 1 } }
            ]
        },
        {
            question: "Your preferred coding environment is:",
            options: [
                { text: "Organized IDE with all the extensions and tools", weights: { architect: 3, perfectionist: 2, learner: 1 } },
                { text: "Minimal text editor, keyboard shortcuts only", weights: { hacker: 3, pragmatist: 2, artist: 1 } },
                { text: "Whatever gets the job done fastest", weights: { pragmatist: 3, debugger: 2, hacker: 1 } },
                { text: "Customized setup with aesthetic themes", weights: { artist: 3, perfectionist: 2, innovator: 1 } }
            ]
        },
        {
            question: "How do you approach code reviews?",
            options: [
                { text: "Thorough and detailed, checking every line", weights: { perfectionist: 3, architect: 2, debugger: 1 } },
                { text: "Focus on logic and functionality, skip style nitpicks", weights: { pragmatist: 3, debugger: 2, learner: 1 } },
                { text: "Look for creative solutions and alternative approaches", weights: { innovator: 3, artist: 2, learner: 1 } },
                { text: "Quick scan for obvious issues, trust the coder", weights: { hacker: 3, pragmatist: 2, innovator: 1 } }
            ]
        }
    ];

    const coderTypes = {
        architect: {
            name: "The Architect",
            icon: "🏗️",
            description: "You're a master planner who thinks in systems and structures. Your code is well-organized, scalable, and built to last. You see the big picture and design elegant solutions that stand the test of time.",
            traits: [
                { icon: "📐", label: "Planning", value: "Exceptional" },
                { icon: "🎯", label: "Organization", value: "Masterful" },
                { icon: "🔧", label: "Scalability", value: "Top Priority" },
                { icon: "📚", label: "Documentation", value: "Comprehensive" }
            ]
        },
        debugger: {
            name: "The Debugger",
            icon: "🔍",
            description: "You're a detective at heart, thriving on finding and fixing issues. Your analytical mind excels at tracing problems to their source. You turn chaos into clarity with patience and precision.",
            traits: [
                { icon: "🧩", label: "Problem Solving", value: "Elite" },
                { icon: "🎯", label: "Attention to Detail", value: "Sharp" },
                { icon: "⚡", label: "Debugging Speed", value: "Lightning Fast" },
                { icon: "🛠️", label: "Tool Mastery", value: "Advanced" }
            ]
        },
        innovator: {
            name: "The Innovator",
            icon: "💡",
            description: "You're driven by creativity and pushing boundaries. Conventional solutions bore you - you'd rather explore new possibilities and create something that's never been done before. You're the future of tech.",
            traits: [
                { icon: "🚀", label: "Innovation", value: "Cutting Edge" },
                { icon: "🎨", label: "Creativity", value: "Boundless" },
                { icon: "🔬", label: "Experimentation", value: "Constant" },
                { icon: "⚡", label: "Risk Taking", value: "Bold" }
            ]
        },
        pragmatist: {
            name: "The Pragmatist",
            icon: "⚙️",
            description: "You're results-oriented and efficiency-focused. You know when to use the right tool for the job and when 'good enough' is perfect. Your code ships on time and solves real problems.",
            traits: [
                { icon: "🎯", label: "Efficiency", value: "Optimized" },
                { icon: "⏱️", label: "Time Management", value: "Excellent" },
                { icon: "📦", label: "Delivery", value: "Reliable" },
                { icon: "🔨", label: "Practicality", value: "Grounded" }
            ]
        },
        perfectionist: {
            name: "The Perfectionist",
            icon: "✨",
            description: "You craft code like an artisan, where every detail matters. Your standards are impossibly high, but the results speak for themselves. Quality isn't a goal - it's your baseline.",
            traits: [
                { icon: "💎", label: "Code Quality", value: "Pristine" },
                { icon: "🎨", label: "Standards", value: "Uncompromising" },
                { icon: "🔍", label: "Attention", value: "Microscopic" },
                { icon: "⚡", label: "Refactoring", value: "Continuous" }
            ]
        },
        artist: {
            name: "The Artist",
            icon: "🎨",
            description: "You see code as a canvas for creative expression. Your solutions are elegant, your interfaces beautiful, and your code reads like poetry. You prove that engineering and artistry can coexist.",
            traits: [
                { icon: "🌈", label: "Aesthetics", value: "Beautiful" },
                { icon: "💫", label: "User Experience", value: "Delightful" },
                { icon: "🎭", label: "Expression", value: "Unique" },
                { icon: "✨", label: "Polish", value: "Refined" }
            ]
        },
        hacker: {
            name: "The Hacker",
            icon: "⚡",
            description: "You thrive in the fast-paced world of rapid prototyping and creative problem-solving. Rules are guidelines, and you find unconventional solutions that just work. You make magic happen.",
            traits: [
                { icon: "🚀", label: "Speed", value: "Blazing" },
                { icon: "🎯", label: "Resourcefulness", value: "Infinite" },
                { icon: "🔥", label: "Adaptability", value: "Supreme" },
                { icon: "💥", label: "Impact", value: "Immediate" }
            ]
        },
        learner: {
            name: "The Eternal Learner",
            icon: "📚",
            description: "You're fueled by curiosity and the joy of mastering new skills. Every project is a chance to grow, every bug a lesson. Your knowledge compounds daily, making you unstoppable.",
            traits: [
                { icon: "🧠", label: "Knowledge", value: "Growing" },
                { icon: "🎓", label: "Curiosity", value: "Insatiable" },
                { icon: "📖", label: "Learning Speed", value: "Rapid" },
                { icon: "🌱", label: "Growth Mindset", value: "Strong" }
            ]
        }
    };

    let currentPersonalityQuestion = 0;
    let personalityAnswers = [];
    let personalityScores = {
        architect: 0,
        debugger: 0,
        innovator: 0,
        pragmatist: 0,
        perfectionist: 0,
        artist: 0,
        hacker: 0,
        learner: 0
    };

    function showPersonalityStatus(message, type = 'info') {
        const container = document.getElementById('personality-status-container');
        let bgColor = '#2a2a40';
        let textColor = '#8b9dff';
        let borderColor = '#667eea';
        
        if (type === 'error') {
            bgColor = 'rgba(231, 76, 60, 0.2)';
            textColor = '#e74c3c';
            borderColor = '#e74c3c';
        } else if (type === 'success') {
            bgColor = 'rgba(39, 174, 96, 0.2)';
            textColor = '#27ae60';
            borderColor = '#27ae60';
        }
        
        container.innerHTML = `<div style="background: ${bgColor}; color: ${textColor}; padding: 1em; border-radius: 10px; margin-bottom: 1.5em; border: 2px solid ${borderColor}; text-align: center;">${message}</div>`;
        setTimeout(() => container.innerHTML = '', 5000);
    }

    function displayPersonalityQuestion() {
        const question = personalityQuestions[currentPersonalityQuestion];
        const container = document.getElementById('personality-question-container');
        
        container.innerHTML = `
            <div class="quiz-question">
                <div style="color: #667eea; font-size: 0.9em; font-weight: bold; margin-bottom: 0.5em;">Question ${currentPersonalityQuestion + 1} of ${personalityQuestions.length}</div>
                <h3 style="color: #e0e0e0; font-size: 1.3em; margin-bottom: 1.5em; line-height: 1.6;">${question.question}</h3>
                <div style="display: flex; flex-direction: column; gap: 1em;">
                    ${question.options.map((option, index) => `
                        <div class="quiz-option" onclick="selectPersonalityAnswer(${index})" style="cursor: pointer; transition: all 0.3s;">
                            ${option.text}
                        </div>
                    `).join('')}
                </div>
            </div>
        `;

        updatePersonalityProgress();
    }

    function selectPersonalityAnswer(optionIndex) {
        const options = document.querySelectorAll('#personality-question-container .quiz-option');
        options.forEach((opt, idx) => {
            if (idx === optionIndex) {
                opt.style.background = '#667eea';
                opt.style.color = 'white';
                opt.style.borderColor = '#8b9dff';
                opt.style.transform = 'scale(1.02)';
            } else {
                opt.style.background = '#1f1f35';
                opt.style.color = '#c0c0c0';
                opt.style.borderColor = '#667eea';
                opt.style.transform = 'scale(1)';
            }
        });

        personalityAnswers[currentPersonalityQuestion] = optionIndex;
        document.getElementById('personality-next-btn').disabled = false;

        const weights = personalityQuestions[currentPersonalityQuestion].options[optionIndex].weights;
        Object.keys(weights).forEach(type => {
            personalityScores[type] = (personalityScores[type] || 0) + weights[type];
        });
    }

    function updatePersonalityProgress() {
        const progress = ((currentPersonalityQuestion + 1) / personalityQuestions.length) * 100;
        document.getElementById('personality-progress').style.width = progress + '%';
        document.getElementById('personality-progress').textContent = Math.round(progress) + '%';
    }

    function nextPersonalityQuestion() {
        currentPersonalityQuestion++;
        
        if (currentPersonalityQuestion < personalityQuestions.length) {
            displayPersonalityQuestion();
            document.getElementById('personality-next-btn').disabled = true;
        } else {
            showPersonalityResults();
        }
    }

    function showPersonalityResults() {
        const topType = Object.keys(personalityScores).reduce((a, b) => personalityScores[a] > personalityScores[b] ? a : b);
        const result = coderTypes[topType];

        document.getElementById('personality-quiz-section').style.display = 'none';
        document.getElementById('personality-result-section').style.display = 'block';

        document.getElementById('personality-result-icon').textContent = result.icon;
        document.getElementById('personality-result-name').textContent = result.name;
        document.getElementById('personality-result-description').innerHTML = `<p>${result.description}</p>`;

        const traitsContainer = document.getElementById('personality-traits-container');
        traitsContainer.innerHTML = result.traits.map(trait => `
            <div class="stat-card">
                <div style="font-size: 2em; margin-bottom: 0.3em;">${trait.icon}</div>
                <div class="stat-label">${trait.label}</div>
                <div style="color: #8b9dff; font-size: 1.2em; font-weight: bold; margin-top: 0.3em;">${trait.value}</div>
            </div>
        `).join('');

        window.coderTypeResult = {
            type: topType,
            name: result.name,
            scores: personalityScores
        };
    }

    async function savePersonalityToProfile() {
        if (!window.coderTypeResult) {
            showPersonalityStatus('No results to save!', 'error');
            return;
        }

        // Get JWT token from cookie
        function getCookie(name) {
            const value = `; ${document.cookie}`;
            const parts = value.split(`; ${name}=`);
            if (parts.length === 2) return parts.pop().split(';').shift();
            return null;
        }

        const token = getCookie('jwt');
        
        if (!token) {
            showPersonalityStatus('⚠️ Please log in to save your personality type', 'error');
            return;
        }

        try {
            showPersonalityStatus('💾 Saving to your profile...', 'info');

            const response = await fetch('/api/match/add', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json',
                    'Authorization': `Bearer ${token}`
                },
                body: JSON.stringify({
                    index: 'coder_type',
                    data: window.coderTypeResult
                })
            });

            const data = await response.json();

            if (response.ok) {
                showPersonalityStatus('✅ Successfully saved to your profile! Your coder type is now part of your matchmaking profile.', 'success');
            } else {
                showPersonalityStatus(`❌ Error: ${data.message}`, 'error');
            }
        } catch (error) {
            showPersonalityStatus(`❌ Failed to save: ${error.message}`, 'error');
        }
    }

    function restartPersonalityQuiz() {
        currentPersonalityQuestion = 0;
        personalityAnswers = [];
        personalityScores = {
            architect: 0,
            debugger: 0,
            innovator: 0,
            pragmatist: 0,
            perfectionist: 0,
            artist: 0,
            hacker: 0,
            learner: 0
        };
        
        document.getElementById('personality-quiz-section').style.display = 'block';
        document.getElementById('personality-result-section').style.display = 'none';
        document.getElementById('personality-next-btn').disabled = true;
        
        displayPersonalityQuestion();
    }

    // Initialize personality quiz when the page loads
    window.addEventListener('DOMContentLoaded', function() {
        if (document.getElementById('personality-question-container')) {
            displayPersonalityQuestion();
        }
    });
</script>

---