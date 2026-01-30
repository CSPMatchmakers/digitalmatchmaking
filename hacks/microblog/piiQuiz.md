---
layout: post
title: "Microblogging Multiple Choice"
description: "Microblog Multiple Choice Quiz for Microblogging Planet"
permalink: /mcq/
parent: "AI Usage"
team: "Unzippers"
submodule: 1
categories: [CSP, Submodule, Microblogging]
tags: [microblogging, submodule, unzippers]
author: "Krishna Visvanath, Sloane Sommers"
date: 2025-10-21
breadcrumb: true
---

# Submodule 1

# Learn about PII!

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Security Protocol Training</title>
    <style>
        .back-button {
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
            padding: 0.5rem 1rem;
            background: #161b22;
            border: 1px solid #30363d;
            border-radius: 6px;
            color: #8b949e;
            text-decoration: none;
            font-size: 0.9rem;
            transition: all 0.2s ease;
            margin-bottom: 1rem;
        }

        .back-button:hover {
            background: #21262d;
            border-color: #30363d;
            color: #c9d1d9;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Courier New', monospace;
            background: #0d1117;
            color: #8b949e;
            padding: 20px;
            min-height: 100vh;
            position: relative;
        }

        body::before {
            content: '';
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: repeating-linear-gradient(
                0deg,
                rgba(100, 120, 130, 0.03) 0px,
                transparent 1px,
                transparent 2px,
                rgba(100, 120, 130, 0.03) 3px
            );
            pointer-events: none;
            z-index: 1;
        }

        .quiz-container {
            max-width: 800px;
            margin: 0 auto;
            background: rgba(22, 27, 34, 0.85);
            padding: 30px;
            border-radius: 6px;
            border: 1px solid #30363d;
            box-shadow: 0 8px 24px rgba(0, 0, 0, 0.4);
            backdrop-filter: blur(10px);
            position: relative;
            z-index: 2;
        }

        #question {
            color: #8b949e;
            font-size: 1.3em;
            font-weight: 400;
            margin-bottom: 25px;
            text-shadow: 0 0 8px rgba(139, 148, 158, 0.2);
            font-family: 'Courier New', monospace;
        }

        .options {
            display: grid;
            gap: 12px;
            margin: 20px 0;
        }

        button {
            padding: 14px 20px;
            cursor: pointer;
            border: 1px solid #30363d;
            border-radius: 4px;
            background: rgba(48, 54, 61, 0.2);
            color: #8b949e;
            font-size: 16px;
            font-weight: 400;
            transition: all 0.2s ease;
            position: relative;
            overflow: hidden;
            font-family: 'Courier New', monospace;
        }

        button::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(100, 120, 130, 0.1), transparent);
            transition: left 0.6s;
        }

        button:hover::before {
            left: 100%;
        }

        button:hover {
            background: rgba(48, 54, 61, 0.4);
            border-color: #485662;
            box-shadow: 0 0 10px rgba(100, 120, 130, 0.2);
        }

        button:disabled {
            opacity: 0.4;
            cursor: not-allowed;
            transform: none;
        }

        button:disabled:hover {
            background: rgba(48, 54, 61, 0.2);
            box-shadow: none;
            border-color: #30363d;
        }

        .option-button {
            text-align: left;
        }

        .option-button.selected {
            background: rgba(72, 86, 98, 0.3);
            border-color: #6e7681;
            box-shadow: 0 0 8px rgba(110, 118, 129, 0.3);
        }

        #submit {
            width: 100%;
            margin-top: 10px;
            background: rgba(48, 54, 61, 0.3);
            font-weight: 400;
            text-transform: uppercase;
            letter-spacing: 2px;
        }

        #submit:hover:not(:disabled) {
            background: rgba(48, 54, 61, 0.5);
        }

        .result {
            margin-top: 20px;
            font-weight: 400;
            font-size: 1.5em;
            color: #7d8590;
            text-align: center;
            text-shadow: 0 0 8px rgba(125, 133, 144, 0.2);
            font-family: 'Courier New', monospace;
        }

        .text-input {
            padding: 14px;
            font-size: 16px;
            border: 1px solid #30363d;
            border-radius: 4px;
            width: 100%;
            box-sizing: border-box;
            margin: 10px 0;
            background: rgba(13, 17, 23, 0.8);
            color: #8b949e;
            font-family: 'Courier New', monospace;
        }

        .text-input:focus {
            outline: none;
            border-color: #485662;
            box-shadow: 0 0 8px rgba(72, 86, 98, 0.3);
            background: rgba(13, 17, 23, 0.95);
        }

        .text-input::placeholder {
            color: #484f58;
        }

        .select-input {
            padding: 14px;
            font-size: 16px;
            border: 1px solid #30363d;
            border-radius: 4px;
            width: 100%;
            box-sizing: border-box;
            margin: 10px 0;
            background: rgba(13, 17, 23, 0.8);
            color: #8b949e;
            font-family: 'Courier New', monospace;
            cursor: pointer;
        }

        .select-input:focus {
            outline: none;
            border-color: #485662;
            box-shadow: 0 0 8px rgba(72, 86, 98, 0.3);
            background: rgba(13, 17, 23, 0.95);
        }

        .select-input option {
            background: #0d1117;
            color: #8b949e;
        }

        .profile-item {
            background: rgba(22, 27, 34, 0.6);
            padding: 15px;
            margin: 12px 0;
            border-radius: 4px;
            border-left: 2px solid #30363d;
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.2);
        }

        .profile-item-label {
            font-weight: 400;
            color: #7d8590;
            margin-bottom: 8px;
            font-size: 0.85em;
            text-transform: uppercase;
            letter-spacing: 1px;
            font-family: 'Courier New', monospace;
        }

        .profile-item-value {
            color: #8b949e;
            word-break: break-word;
            font-size: 1em;
            font-family: 'Courier New', monospace;
        }

        .breather-container {
            text-align: center;
            padding: 30px;
            margin: 20px 0;
            background: rgba(22, 27, 34, 0.8);
            border-radius: 4px;
            border: 1px solid #30363d;
            box-shadow: 0 4px 16px rgba(0, 0, 0, 0.3);
        }

        .breather-message {
            color: #8b949e;
            font-size: 1.2em;
            margin-bottom: 20px;
            font-weight: 400;
            text-shadow: 0 0 8px rgba(139, 148, 158, 0.2);
            line-height: 1.6;
            font-family: 'Courier New', monospace;
        }

        .breather-buttons {
            display: flex;
            gap: 15px;
            justify-content: center;
            flex-wrap: wrap;
        }

        .warning-message {
            background: rgba(60, 30, 30, 0.3);
            border: 1px solid #6e4040;
            border-radius: 4px;
            padding: 20px;
            margin: 20px 0;
            color: #b58181;
            font-weight: 400;
            text-align: center;
            box-shadow: 0 0 12px rgba(110, 64, 64, 0.2);
        }

        #leakContinue:disabled {
            background: rgba(30, 35, 40, 0.2);
            border-color: #30363d;
            color: #484f58;
        }

        @keyframes pulse {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.6; }
        }

        .loading {
            animation: pulse 1.5s infinite;
        }

        @media (max-width: 768px) {
            .quiz-container {
                padding: 20px;
            }

            #question {
                font-size: 1.1em;
            }

            button {
                padding: 12px 16px;
                font-size: 14px;
            }

            .breather-buttons {
                flex-direction: column;
            }

            .breather-buttons button {
                width: 100%;
            }
        }
    </style>
</head>
<body>
    <a href="/digitalmatchmaking/home/" class="back-button">← Back</a>

    <div class="quiz-container">
        <!-- Quiz Mode Selector Modal -->
        <div id="modeSelector" style="text-align: center; padding: 60px 20px;">
            <h2 style="color: #8b949e; font-size: 1.8em; margin-bottom: 40px; font-family: 'Courier New', monospace;">
                Choose Your Path
            </h2>
            <div style="display: flex; gap: 20px; flex-direction: column; max-width: 600px; margin: 0 auto;">
                <button class="option-button" id="piiModeBtn" onclick="selectMode('pii')" style="padding: 20px; font-size: 1.1em; cursor: pointer; transition: all 0.3s ease;">
                    📋 Fill Out Your Profile
                    <div style="font-size: 0.85em; color: #6e7681; margin-top: 8px;">
                        Answer security protocol questions and build your profile
                    </div>
                </button>
                <button class="option-button" id="matchmakingModeBtn" onclick="selectMode('matchmaking')" style="padding: 20px; font-size: 1.1em; cursor: pointer; transition: all 0.3s ease;">
                    💕 Find Your Personality Type
                    <div style="font-size: 0.85em; color: #6e7681; margin-top: 8px;">
                        Discover your unique personality through our matchmaking quiz
                    </div>
                </button>
            </div>
        </div>
        <!-- PII Quiz Container -->
        <div id="piiQuizContainer" style="display: none;">
        <div id="loadingCheck" style="text-align: center; padding: 40px;">
            <div class="loading" style="font-size: 1.2em; color: #7d8590; font-family: 'Courier New', monospace;">
                CHECKING SYSTEM RECORDS...
            </div>
        </div>
        <div id="existingProfilePrompt" style="display: none;">
            <div class="breather-container">
                <div class="breather-message">EXISTING PROFILE DETECTED</div>
                <p style="color: #6e7681; margin: 20px 0; font-family: 'Courier New', monospace;">
                    Would you like to review your existing profile or retake the assessment?
                </p>
                <div class="breather-buttons">
                    <button id="loadExistingProfile" class="option-button">Load Existing Profile</button>
                    <button id="retakeFromStart" class="option-button">Retake Assessment</button>
                </div>
            </div>
        </div>
        <div id="quiz" style="display: none;">
            <div id="question"></div>
            <div class="options" id="options"></div>
            <button id="submit" type="button">Submit Answer</button>
        </div>
        <div id="results" style="display: none;">
            <div class="result">Assessment Complete: <span id="score">0</span>/10</div>
            <button id="restart">Restart Assessment</button>
        </div>
        <div id="leakBreather" style="display: none;">
            <div class="breather-container warning-message">
                <div class="breather-message" id="leakMessage"></div>
                <div class="breather-buttons">
                    <button id="leakRetake" class="option-button">Retake Assessment</button>
                    <button id="leakContinue" class="option-button">Continue to Profile</button>
                </div>
            </div>
        </div>
        <div id="review" style="display: none;">
            <div class="result">Profile Data Summary</div>
            <div id="profileData"></div>
            <div class="options">
                <button id="saveProfile" class="option-button">Save Profile</button>
                <button id="retakeQuiz" class="option-button">Retake Assessment</button>
            </div>
        </div>
        </div><!-- End piiQuizContainer -->

        <!-- Matchmaking Personality Quiz Container -->
        <div id="matchmakingQuizContainer" style="display: none;">
            <!-- Matchmaking quiz will be injected here via JavaScript -->
        </div>
    </div>

    <script type="module">
        import { pythonURI, fetchOptions } from '/digitalmatchmaking/assets/js/api/config.js';
        window._piiImportedConfig = window._piiImportedConfig || {};
        if (pythonURI) window._piiImportedConfig.pythonURI = pythonURI;
        if (fetchOptions) window._piiImportedConfig.fetchOptions = fetchOptions;
        
        // Quiz mode selector
        window.selectMode = async function(mode) {
            const modeSelector = document.getElementById('modeSelector');
            const piiContainer = document.getElementById('piiQuizContainer');
            const matchmakingContainer = document.getElementById('matchmakingQuizContainer');
            
            modeSelector.style.display = 'none';
            
            if (mode === 'pii') {
                piiContainer.style.display = 'block';
                matchmakingContainer.style.display = 'none';
                // Initialize PII quiz - directly call checkExistingProfile
                console.log('PII mode selected, checking for existing profile...');
                await checkExistingProfile();
            } else if (mode === 'matchmaking') {
                piiContainer.style.display = 'none';
                matchmakingContainer.style.display = 'block';
                // Initialize matchmaking quiz
                setTimeout(() => {
                    if (typeof initMatchmakingQuiz === 'function') {
                        initMatchmakingQuiz();
                    }
                }, 100);
            }
        };
        
        const questions = [
            {
                question: "What does PII stand for?",
                options: ["Peer Investigation Information", "Personally Identifiable Information", "Please Invert Intestine", "Personal Identifying Infirmary"],
                correct: 1
            },
            {
                question: "Why do we protect PII?",
                options: ["Because mean people want to stop us from making friends", "Because we're mysterious and nonchalant, sharing PII would diminish that", "To prevent hackers, scammers, and others with ill intent from harming us", "Because Kai Cenat told us to"],
                correct: 2
            },
            {
                isBreather: true,
                message: "Protocol acknowledged. Now proceed with profile registration to establish your network identity."
            },
            {
                question: "What is your favorite color?",
                options: ["Red", "Orange", "Yellow", "Green", "Blue", "Purple", "Black", "White"],
                correct: null,
                allowDropdown: true
            },
            {
                question: "What do you want your username to be?",
                allowTextEntry: true,
                correct: null 
            },
            {
                question: "What's your favorite animal?",
                options: ["Dogs", "Cats", "Birds", "Fish", "Reptiles"],
                correct: null
            },
            {
                question: "What is your full name?",
                allowTextEntry: true,
                correct: null
            },
            {
                question: "What is your favorite genre of music?",
                options: ["Rock", "Pop", "Rap"],
                correct: null
            },
            {
                question: "What is your favorite band/musical artist?",
                allowTextEntry: true,
                correct: null 
            },
            {
                question: "What is your SSN?",
                allowTextEntry: true,
                correct: null
            },
            {
                question: "Where do you live?",
                allowTextEntry: true,
                correct: null
            },
            {
                question: "What is your favorite subject?",
                options: ["Math", "Science", "English", "History"],
                correct: null
            },
        ];

        let currentQuestion = 0;
        let score = 0;
        let selectedOption = null;

        const questionEl = document.getElementById('question');
        const optionsEl = document.getElementById('options');
        const submitBtn = document.getElementById('submit');
        const quizEl = document.getElementById('quiz');
        const resultsEl = document.getElementById('results');
        const scoreEl = document.getElementById('score');
        const restartBtn = document.getElementById('restart');
        const reviewEl = document.getElementById('review');
        const profileDataEl = document.getElementById('profileData');
        const saveProfileBtn = document.getElementById('saveProfile');
        const retakeQuizBtn = document.getElementById('retakeQuiz');
        const leakBreatherEl = document.getElementById('leakBreather');
        const leakMessageEl = document.getElementById('leakMessage');
        const leakRetakeBtn = document.getElementById('leakRetake');
        const leakContinueBtn = document.getElementById('leakContinue');
        const loadingCheckEl = document.getElementById('loadingCheck');
        const existingProfilePromptEl = document.getElementById('existingProfilePrompt');
        const loadExistingProfileBtn = document.getElementById('loadExistingProfile');
        const retakeFromStartBtn = document.getElementById('retakeFromStart');

        let existingProfileData = null;

        async function checkExistingProfile() {
            const importedCfg = window._piiImportedConfig || {};
            const pythonURI = importedCfg.pythonURI || window.pythonURI || '';
            const globalFetchOptions = importedCfg.fetchOptions || window.fetchOptions || {};

            // Use /api/match/data instead of /api/match/save since it supports GET
            const endpoint = pythonURI ? `${pythonURI}/api/match/data` : '/api/match/data';

            console.log('=== PROFILE CHECK DEBUG ===');
            console.log('pythonURI:', pythonURI);
            console.log('Full endpoint:', endpoint);
            console.log('Fetch options:', globalFetchOptions);

            const options = Object.assign({}, globalFetchOptions, {
                method: 'GET',
                credentials: (globalFetchOptions && globalFetchOptions.credentials) ? globalFetchOptions.credentials : 'include'
            });

            console.log('Request options:', options);

            try {
                console.log('Sending GET request to:', endpoint);
                const response = await fetch(endpoint, options);
                console.log('Response status:', response.status);
                console.log('Response statusText:', response.statusText);
                console.log('Response headers:', Object.fromEntries([...response.headers.entries()]));
                
                const responseText = await response.text();
                console.log('Response body (raw):', responseText);
                
                if (response.ok) {
                    const data = JSON.parse(responseText);
                    console.log('Parsed response data:', data);
                    console.log('Type of data:', typeof data);
                    
                    // The /data endpoint returns { message: ..., data: { profile: {...}, personality_quiz_responses: ... } }
                    // We need to check if data.data.profile.profile_quiz exists
                    const profileSection = data.data && data.data.profile;
                    const profileQuiz = profileSection && profileSection.profile_quiz;
                    
                    console.log('data.data:', data.data);
                    console.log('profileSection:', profileSection);
                    console.log('profileQuiz:', profileQuiz);
                    
                    if (profileQuiz && typeof profileQuiz === 'object' && Object.keys(profileQuiz).length > 0) {
                        // Store the profile data
                        existingProfileData = profileQuiz;
                        console.log('✅ PROFILE FOUND! Stored existing profile data:', existingProfileData);
                        console.log('Hiding loading, showing prompt...');
                        
                        loadingCheckEl.style.display = 'none';
                        existingProfilePromptEl.style.display = 'block';
                        console.log('loadingCheckEl display:', loadingCheckEl.style.display);
                        console.log('existingProfilePromptEl display:', existingProfilePromptEl.style.display);
                        return profileQuiz;
                    } else {
                        console.log('❌ Profile quiz not found in response');
                    }
                } else if (response.status === 404) {
                    console.log('404 - Profile not found (expected for new users)');
                } else {
                    console.log(`Unexpected status code: ${response.status}`);
                }
                
                console.log('No existing profile, starting quiz');
                loadingCheckEl.style.display = 'none';
                quizEl.style.display = 'block';
                displayQuestion();
                return null;
            } catch (err) {
                console.error('Error checking profile:', err);
                console.error('Error stack:', err.stack);
                console.log('Starting fresh assessment');
                loadingCheckEl.style.display = 'none';
                quizEl.style.display = 'block';
                displayQuestion();
                return null;
            }
        }

        loadExistingProfileBtn.onclick = () => {
            console.log('Load existing profile clicked, data:', existingProfileData);
            if (existingProfileData) {
                displayExistingProfile(existingProfileData);
            } else {
                console.error('No existing profile data available');
                alert('Error: Profile data not found');
            }
        };

        retakeFromStartBtn.onclick = () => {
            existingProfilePromptEl.style.display = 'none';
            quizEl.style.display = 'block';
            currentQuestion = 0;
            score = 0;
            selectedOption = null;
            displayQuestion();
        };

        function displayExistingProfile(profileData) {
            existingProfilePromptEl.style.display = 'none';
            quizEl.style.display = 'none';
            reviewEl.style.display = 'block';

            profileDataEl.innerHTML = '';
            
            // profileData is now an object with question-response pairs
            for (let [question, response] of Object.entries(profileData)) {
                const profileItem = document.createElement('div');
                profileItem.className = 'profile-item';
                const label = document.createElement('div');
                label.className = 'profile-item-label';
                label.textContent = question;
                const value = document.createElement('div');
                value.className = 'profile-item-value';
                value.textContent = response;
                profileItem.appendChild(label);
                profileItem.appendChild(value);
                profileDataEl.appendChild(profileItem);
            }
        }

        function displayQuestion() {
            const question = questions[currentQuestion];
            questionEl.textContent = question.question;
            questionEl.style.textAlign = '';
            questionEl.style.fontSize = '';
            questionEl.style.marginBottom = '';
            submitBtn.style.display = 'block';
            
            optionsEl.innerHTML = '';
            
            if (question.isBreather) {
                questionEl.textContent = question.message;
                questionEl.style.textAlign = 'center';
                questionEl.style.fontSize = '1.2em';
                questionEl.style.marginBottom = '30px';
                
                const continueBtn = document.createElement('button');
                continueBtn.className = 'option-button';
                continueBtn.textContent = 'Continue';
                continueBtn.onclick = () => {
                    currentQuestion++;
                    selectedOption = null;
                    displayQuestion();
                };
                optionsEl.appendChild(continueBtn);
                submitBtn.style.display = 'none';
            } else if (question.allowTextEntry) {
                const textInput = document.createElement('input');
                textInput.type = 'text';
                textInput.className = 'text-input';
                textInput.placeholder = "Enter your response or decline to answer";
                textInput.oninput = () => {
                    submitBtn.disabled = textInput.value.trim() === '';
                };
                optionsEl.appendChild(textInput);
                
                const declineBtn = document.createElement('button');
                declineBtn.className = 'option-button';
                declineBtn.textContent = "I'd rather not answer";
                declineBtn.onclick = () => {
                    textInput.value = '';
                    question.userResponse = null;
                    submitBtn.disabled = false;
                    declineBtn.classList.add('selected');
                };
                optionsEl.appendChild(declineBtn);
                
                submitBtn.style.display = 'block';
                submitBtn.disabled = true;
                questions[currentQuestion].textInputElement = textInput;
            } else if (question.allowDropdown) {
                // Create dropdown menu for this question
                const selectInput = document.createElement('select');
                selectInput.className = 'select-input';
                
                // Add default/placeholder option
                const defaultOption = document.createElement('option');
                defaultOption.value = '';
                defaultOption.textContent = 'Select a color...';
                defaultOption.disabled = true;
                defaultOption.selected = true;
                selectInput.appendChild(defaultOption);
                
                // Add all color options
                question.options.forEach((option, index) => {
                    const optionEl = document.createElement('option');
                    optionEl.value = index;
                    optionEl.textContent = option;
                    selectInput.appendChild(optionEl);
                });
                
                selectInput.onchange = () => {
                    selectedOption = parseInt(selectInput.value);
                    submitBtn.disabled = false;
                };
                
                optionsEl.appendChild(selectInput);
                submitBtn.style.display = 'block';
                submitBtn.disabled = true;
                questions[currentQuestion].selectElement = selectInput;
            } else {
                submitBtn.style.display = 'block';
                question.options.forEach((option, index) => {
                    const button = document.createElement('button');
                    button.className = 'option-button';
                    button.textContent = option;
                    button.onclick = () => selectOption(index);
                    optionsEl.appendChild(button);
                });
                submitBtn.disabled = true;
            }
        }

        function selectOption(index) {
            const buttons = optionsEl.getElementsByClassName('option-button');
            for (let button of buttons) {
                button.classList.remove('selected');
            }
            buttons[index].classList.add('selected');
            selectedOption = index;
            submitBtn.disabled = false;
        }

        function submitAnswer() {
            const question = questions[currentQuestion];
            
            if (question.allowTextEntry) {
                const textInput = question.textInputElement || document.querySelector('.text-input');
                if (textInput && textInput.value.trim() !== '') {
                    question.userResponse = textInput.value.trim();
                } else if (question.userResponse === undefined) {
                    question.userResponse = null;
                }
            } else if (question.allowDropdown) {
                const selectInput = question.selectElement || document.querySelector('.select-input');
                if (selectInput && selectInput.value !== '') {
                    const index = parseInt(selectInput.value);
                    question.userResponse = question.options[index];
                } else if (question.userResponse === undefined) {
                    question.userResponse = null;
                }
            } else {
                if (selectedOption !== null && question.options && question.options[selectedOption] !== undefined) {
                    question.userResponse = question.options[selectedOption];
                } else if (question.userResponse === undefined) {
                    question.userResponse = null;
                }

                if (typeof question.correct === 'number' && selectedOption === question.correct) {
                    score++;
                }
            }
            
            currentQuestion++;
            if (currentQuestion < questions.length) {
                selectedOption = null;
                displayQuestion();
            } else {
                showResults();
            }
        }

        function showResults() {
            quizEl.style.display = 'none';
            resultsEl.style.display = 'none';
            reviewEl.style.display = 'none';
            
            // MODIFIED: Collect only non-personal, non-null responses
            const userDataResponses = {};
            const startIndex = 3;
            
            // Define which questions are safe to save (by index relative to startIndex)
            const safeQuestionIndices = [0, 1, 2, 4, 5, 8]; // favorite color, username, favorite animal, genre, band/artist, favorite subject
            
            for (let i = startIndex; i < questions.length; i++) {
                const q = questions[i];
                const response = q.userResponse !== undefined ? q.userResponse : null;
                const relativeIndex = i - startIndex;
                
                // Only save if it's a safe question and response is not null
                if (safeQuestionIndices.includes(relativeIndex) && response !== null && response !== undefined && String(response).trim() !== '') {
                    userDataResponses[q.question] = response;
                }
            }

            // Check for PII leaks by examining sensitive questions
            let leakCount = 0;
            
            for (let i = startIndex; i < questions.length; i++) {
                const q = questions[i];
                const response = q.userResponse !== undefined ? q.userResponse : null;
                const qLower = (q.question || '').toLowerCase();
                
                if (response !== null && response !== undefined && String(response).trim() !== '') {
                    if (qLower.includes('full name') || qLower.includes('ssn') || qLower.includes('where do you live') || qLower.includes('ip')) {
                        leakCount++;
                    }
                }
            }

            const userDataJSON = JSON.stringify(userDataResponses, null, 2);
            sessionStorage.setItem('userQuizResponses', userDataJSON);
            window.userQuizData = userDataJSON;

            if (leakCount > 0) {
                leakMessageEl.textContent = `⚠️ SECURITY BREACH DETECTED ⚠️\n\nYou exposed ${leakCount} piece${leakCount>1? 's' : ''} of sensitive personal information! This data could be exploited by hostile actors. Retake the assessment and demonstrate proper security protocols.`;
                leakBreatherEl.style.display = 'block';
                reviewEl.style.display = 'none';
                leakContinueBtn.disabled = true;

                leakRetakeBtn.onclick = () => {
                    leakBreatherEl.style.display = 'none';
                    restartQuiz();
                };
                return;
            }

            leakBreatherEl.style.display = 'none';
            leakContinueBtn.disabled = false;

            // Display profile data with questions for review (but only responses will be saved)
            profileDataEl.innerHTML = '';
            
            // Display the saved data
            for (let [question, response] of Object.entries(userDataResponses)) {
                const profileItem = document.createElement('div');
                profileItem.className = 'profile-item';
                const label = document.createElement('div');
                label.className = 'profile-item-label';
                label.textContent = question;
                const value = document.createElement('div');
                value.className = 'profile-item-value';
                value.textContent = response;
                profileItem.appendChild(label);
                profileItem.appendChild(value);
                profileDataEl.appendChild(profileItem);
            }
            reviewEl.style.display = 'block';
        }

        function restartQuiz() {
            currentQuestion = 0;
            score = 0;
            selectedOption = null;
            quizEl.style.display = 'block';
            resultsEl.style.display = 'none';
            reviewEl.style.display = 'none';
            displayQuestion();
        }

        saveProfileBtn.onclick = async () => {
            const userDataJSON = sessionStorage.getItem('userQuizResponses');
            if (!userDataJSON) {
                alert("No profile data found to save.");
                return;
            }

            let profileData;
            try {
                profileData = JSON.parse(userDataJSON);
            } catch (err) {
                console.error('piiQuiz: invalid JSON in sessionStorage userQuizResponses', err, userDataJSON);
                alert('Saved responses are not valid JSON. Please retake quiz.');
                return;
            }

            const importedCfg = window._piiImportedConfig || {};
            const pythonURI = importedCfg.pythonURI || window.pythonURI || '';
            const globalFetchOptions = importedCfg.fetchOptions || window.fetchOptions || {};

            const endpoint = pythonURI ? `${pythonURI}/api/match/save` : '/api/match/save';

            const mergedHeaders = Object.assign({}, (globalFetchOptions.headers || {}), {
                'Content-Type': 'application/json'
            });

            // MODIFIED: Send only the array of responses
            const payload = { profile_data: profileData };
            let bodyStr;
            try {
                bodyStr = JSON.stringify(payload);
            } catch (err) {
                console.error('piiQuiz: failed to stringify payload', err);
                alert('Failed to prepare profile JSON: ' + (err && err.message ? err.message : String(err)));
                return;
            }

            console.log('=== SAVE PROFILE DEBUG ===');
            console.log('piiQuiz: Saving to endpoint:', endpoint);
            console.log('piiQuiz: Payload:', payload);
            console.log('piiQuiz: Profile data length:', bodyStr.length);
            console.log('piiQuiz: Headers:', mergedHeaders);

            const options = Object.assign({}, globalFetchOptions, {
                method: 'POST',
                headers: mergedHeaders,
                body: bodyStr
            });

            if (!options.credentials) options.credentials = (globalFetchOptions && globalFetchOptions.credentials) ? globalFetchOptions.credentials : 'include';

            console.log('piiQuiz: Full request options:', options);

            try {
                console.log('piiQuiz: Sending POST request...');
                const response = await fetch(endpoint, options);
                console.log('piiQuiz: Response status:', response.status);
                console.log('piiQuiz: Response statusText:', response.statusText);
                console.log('piiQuiz: Response headers:', Object.fromEntries([...response.headers.entries()]));
                
                const responseText = await response.text();
                console.log('piiQuiz: Response body (raw text):', responseText);
                
                let data = null;
                if (responseText) {
                    try {
                        data = JSON.parse(responseText);
                        console.log('piiQuiz: Response data (parsed):', data);
                    } catch (parseErr) {
                        console.error('piiQuiz: Failed to parse response as JSON:', parseErr);
                        console.log('piiQuiz: Response was:', responseText);
                    }
                }

                if (!response.ok) {
                    alert("Failed to save profile: " + (data && data.message ? data.message : `Status ${response.status}`));
                    console.error("Backend response:", data);
                    return;
                }

                console.log("Profile saved successfully:", data);
                alert("Profile saved successfully! Data is now in database");
            } catch (err) {
                console.error("Error saving profile:", err);
                console.error("Error stack:", err.stack);
                alert("Failed to save profile. Check console for details. Error: " + err.message);
            }
        };

        retakeQuizBtn.onclick = () => {
            restartQuiz();
        };

        submitBtn.onclick = submitAnswer;
        restartBtn.onclick = restartQuiz;

        /* ========== MATCHMAKING QUIZ LOGIC ========== */
        const matchmakingQuestions = [
            { id: 1, question: "At a social gathering, you typically...", options: [{ text: "Seek out new people and enjoy being the center of attention", value: "E_high" }, { text: "Talk to a few close friends and enjoy smaller conversations", value: "I_moderate" }, { text: "Prefer observing and only engage when approached", value: "I_high" }, { text: "Mix between groups and one-on-one conversations", value: "E_moderate" }] },
            { id: 2, question: "When making important decisions, you rely most on...", options: [{ text: "Logic, facts, and objective analysis", value: "T_high" }, { text: "How it will affect people and relationships", value: "F_high" }, { text: "A balance of logic and emotional impact", value: "T_moderate" }, { text: "Gut feeling and personal values", value: "F_moderate" }] },
            { id: 3, question: "Your ideal weekend involves...", options: [{ text: "Spontaneous adventures and seeing where the day takes you", value: "P_high" }, { text: "A well-planned itinerary of activities", value: "J_high" }, { text: "A loose plan with room for flexibility", value: "P_moderate" }, { text: "Structured activities with some downtime built in", value: "J_moderate" }] },
            { id: 4, question: "When learning something new, you prefer...", options: [{ text: "Understanding the big picture and future possibilities", value: "N_high" }, { text: "Hands-on practice with concrete examples", value: "S_high" }, { text: "Starting with theory, then applying it practically", value: "N_moderate" }, { text: "Step-by-step instructions with clear outcomes", value: "S_moderate" }] },
            { id: 5, question: "Describe your ideal date or hangout. What would you do and why?", type: "freeResponse", placeholder: "Share your thoughts..." },
            { id: 6, question: "After a long day, you recharge by...", options: [{ text: "Being alone with your thoughts or hobbies", value: "I_high" }, { text: "Calling friends or going out", value: "E_high" }, { text: "Quiet time first, then maybe socializing", value: "I_moderate" }, { text: "Light social interaction with close ones", value: "E_moderate" }] },
            { id: 7, question: "When someone shares a problem with you, you typically...", options: [{ text: "Offer solutions and practical advice", value: "T_high" }, { text: "Listen empathetically and validate their feelings", value: "F_high" }, { text: "Ask questions to understand before responding", value: "T_moderate" }, { text: "Share similar experiences to show understanding", value: "F_moderate" }] },
            { id: 8, question: "What's something you're passionate about and why does it matter to you?", type: "freeResponse", placeholder: "Tell us about your passion..." },
            { id: 9, question: "When planning a trip, you...", options: [{ text: "Research extensively and create detailed plans", value: "J_high" }, { text: "Book tickets and figure out the rest as you go", value: "P_high" }, { text: "Plan key activities but leave room for spontaneity", value: "P_moderate" }, { text: "Follow recommended itineraries from others", value: "S_moderate" }] },
            { id: 10, question: "In conversations, you tend to focus on...", options: [{ text: "Abstract ideas, theories, and what could be", value: "N_high" }, { text: "Concrete facts, experiences, and what is", value: "S_high" }, { text: "Both practical details and underlying meanings", value: "N_moderate" }, { text: "Real-world applications and examples", value: "S_moderate" }] },
            { id: 11, question: "When facing conflict, you're more likely to...", options: [{ text: "Address it directly with facts and logic", value: "T_high" }, { text: "Consider feelings and find a harmonious solution", value: "F_high" }, { text: "Avoid it unless absolutely necessary", value: "I_high" }, { text: "Seek mediation or a third-party perspective", value: "F_moderate" }] },
            { id: 12, question: "If you could change one thing about the world, what would it be and why?", type: "freeResponse", placeholder: "Share your vision..." },
            { id: 13, question: "Your approach to rules and deadlines is...", options: [{ text: "Strict - rules exist for a reason and should be followed", value: "J_high" }, { text: "Flexible - guidelines that can bend based on context", value: "P_high" }, { text: "Respectful but willing to question when needed", value: "P_moderate" }, { text: "Depends on whether they make logical sense", value: "T_moderate" }] }
        ];
        let matchmakingCurrentQuestion = 0;
        let matchmakingAnswers = {};

        window.initMatchmakingQuiz = function() {
            const container = document.getElementById('matchmakingQuizContainer');
            container.innerHTML = `
                <div style="padding: 20px;">
                    <div style="margin-bottom: 20px;">
                        <div style="width: 100%; height: 8px; background: rgba(255,255,255,0.05); border-radius: 20px; overflow: hidden;">
                            <div id="matchProgress" style="height: 100%; background: linear-gradient(90deg, #ff6b9d 0%, #ff8fab 50%, #ffa3bb 100%); width: 0%; transition: width 0.3s;"></div>
                        </div>
                        <p style="margin: 8px 0 0 0; color: #8b949e; font-size: 0.9em; text-align: center;" id="matchProgressText">Question 1 of ${matchmakingQuestions.length}</p>
                    </div>
                    <div id="matchQuizContent"></div>
                    <div style="display: flex; gap: 10px; margin-top: 20px;">
                        <button id="matchPrevBtn" class="option-button" onclick="matchmakingPrevious()" style="display: none; flex: 1;">← Previous</button>
                        <button id="matchNextBtn" class="option-button" onclick="matchmakingNext()" style="flex: 1;">Next →</button>
                        <button id="matchSubmitBtn" class="option-button" onclick="matchmakingSubmit()" style="display: none; flex: 1;">Get My Type ✨</button>
                    </div>
                </div>
                <div id="matchResults" style="display: none; padding: 20px;">
                    <h3 style="color: #8b949e; text-align: center; margin-bottom: 20px;">💕 Your Personality Type</h3>
                    <div id="matchResultContent"></div>
                </div>
            `;
            matchmakingCurrentQuestion = 0;
            matchmakingAnswers = {};
            renderMatchmakingQuestion();
        };

        window.renderMatchmakingQuestion = function() {
            const q = matchmakingQuestions[matchmakingCurrentQuestion];
            const content = document.getElementById('matchQuizContent');
            let html = `<h3 style="color: #8b949e; margin-bottom: 15px; text-align: center;">${q.question}</h3>`;
            
            if (q.type === 'freeResponse') {
                const saved = matchmakingAnswers[q.id] || '';
                html += `<textarea class="text-input" id="match-free-${q.id}" placeholder="${q.placeholder}" style="width: 100%; padding: 12px; background: rgba(22,27,34,0.6); border: 1px solid #30363d; border-radius: 4px; color: #8b949e; font-family: 'Courier New'; font-size: 0.9em; min-height: 100px;" oninput="matchmakingSaveAnswer(${q.id}, this.value)">${saved}</textarea>`;
            } else {
                q.options.forEach((opt, i) => {
                    const selected = matchmakingAnswers[q.id] === opt.value ? ' selected' : '';
                    html += `<button class="option-button${selected}" onclick="matchmakingSelectOption(${q.id}, '${opt.value}', this)" style="text-align: left; margin: 8px 0; cursor: pointer;">${opt.text}</button>`;
                });
            }
            content.innerHTML = html;
            updateMatchmakingButtons();
        };

        window.matchmakingSelectOption = function(qId, value, btn) {
            matchmakingAnswers[qId] = value;
            document.querySelectorAll('.option-button').forEach(b => b.classList.remove('selected'));
            btn.classList.add('selected');
            updateMatchmakingButtons();
        };

        window.matchmakingSaveAnswer = function(qId, value) {
            matchmakingAnswers[qId] = value.trim();
            updateMatchmakingButtons();
        };

        window.updateMatchmakingButtons = function() {
            const q = matchmakingQuestions[matchmakingCurrentQuestion];
            const hasAnswer = matchmakingAnswers[q.id] && (q.type === 'freeResponse' ? matchmakingAnswers[q.id].length >= 3 : true);
            const prevBtn = document.getElementById('matchPrevBtn');
            const nextBtn = document.getElementById('matchNextBtn');
            const submitBtn = document.getElementById('matchSubmitBtn');
            
            prevBtn.style.display = matchmakingCurrentQuestion > 0 ? 'block' : 'none';
            if (matchmakingCurrentQuestion === matchmakingQuestions.length - 1) {
                nextBtn.style.display = 'none';
                submitBtn.style.display = 'block';
                submitBtn.disabled = !hasAnswer;
            } else {
                nextBtn.style.display = 'block';
                submitBtn.style.display = 'none';
                nextBtn.disabled = !hasAnswer;
            }
            
            const prog = ((matchmakingCurrentQuestion + 1) / matchmakingQuestions.length) * 100;
            document.getElementById('matchProgress').style.width = prog + '%';
            document.getElementById('matchProgressText').textContent = `Question ${matchmakingCurrentQuestion + 1} of ${matchmakingQuestions.length}`;
        };

        window.matchmakingNext = function() {
            if (matchmakingCurrentQuestion < matchmakingQuestions.length - 1) {
                matchmakingCurrentQuestion++;
                renderMatchmakingQuestion();
            }
        };

        window.matchmakingPrevious = function() {
            if (matchmakingCurrentQuestion > 0) {
                matchmakingCurrentQuestion--;
                renderMatchmakingQuestion();
            }
        };

        window.matchmakingSubmit = async function() {
            const responses = matchmakingQuestions.map(q => ({
                question: q.question,
                answer: matchmakingAnswers[q.id] || '',
                type: q.type || 'multipleChoice'
            }));
            
            document.getElementById('matchQuizContent').innerHTML = '<p style="text-align: center; color: #8b949e;">⏳ Analyzing your personality...</p>';
            
            // Save only personality type if backend returns it
            fetch(`${pythonURI}/api/match/add`, {
                method: 'POST',
                credentials: 'include',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify({ index: 'personality_quiz_responses', data: 'Personality Type Analyzed' })
            }).catch(() => {});
            
            document.getElementById('matchResults').style.display = 'block';
            document.getElementById('matchQuizContent').innerHTML = '<p style="text-align: center; color: #4caf50; font-weight: bold;">✅ Your personality analysis has been saved!</p>';
        };
    </script>
</body>
</html>