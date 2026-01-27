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

        .mission-header {
            text-align: center;
            padding: 40px 20px;
            background: linear-gradient(135deg, #161b22 0%, #0d1117 100%);
            border-bottom: 1px solid #30363d;
            margin-bottom: 30px;
            position: relative;
            overflow: hidden;
            border-radius: 6px;
            z-index: 2;
        }

        .mission-header::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(100, 120, 130, 0.05), transparent);
            animation: scan 4s infinite;
        }

        @keyframes scan {
            0% { left: -100%; }
            100% { left: 100%; }
        }

        .glitch-text {
            font-size: 2.5em;
            font-weight: 400;
            color: #7d8590;
            text-transform: uppercase;
            letter-spacing: 4px;
            text-shadow: 0 0 10px rgba(125, 133, 144, 0.3);
            margin-bottom: 20px;
            position: relative;
            z-index: 1;
            font-family: 'Courier New', monospace;
        }

        .mission-brief {
            max-width: 800px;
            margin: 15px auto;
            line-height: 1.8;
            color: #6e7681;
            position: relative;
            z-index: 1;
            font-family: 'Courier New', monospace;
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
            .glitch-text {
                font-size: 1.8em;
            }

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
    <div class="mission-header">
        <h1 class="glitch-text">SECURITY PROTOCOL TRAINING</h1>
        <p class="mission-brief">Complete this security assessment to verify your understanding of Personally Identifiable Information (PII) protocols. Operatives must demonstrate knowledge of data protection standards before accessing the network.</p>
    </div>

    <div class="quiz-container">
        <div id="loadingCheck" style="text-align: center; padding: 40px;">
            <div class="loading" style="font-size: 1.2em; color: #7d8590; font-family: 'Courier New', monospace;">
                CHECKING SYSTEM RECORDS...
            </div>
        </div>
        <div id="existingProfilePrompt" style="display: none;">
            <div class="breather-container">
                <div class="breather-message">EXISTING PROFILE DETECTED</div>
                <p style="color: #6e7681; margin: 20px 0; font-family: 'Courier New', monospace;">
                    We found your previous security clearance records in the system. Would you like to review your existing profile or retake the assessment?
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
    </div>

    <script type="module">
        import { pythonURI, fetchOptions } from '/digitalmatchmaking/assets/js/api/config.js';
        // Populate window._piiImportedConfig so the rest of the script can prefer the imported pythonURI and fetch options.
        window._piiImportedConfig = window._piiImportedConfig || {};
        if (pythonURI) window._piiImportedConfig.pythonURI = pythonURI;
        if (fetchOptions) window._piiImportedConfig.fetchOptions = fetchOptions;
        
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
                correct: null 
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

        // Check for existing profile on page load
        async function checkExistingProfile() {
            const importedCfg = window._piiImportedConfig || {};
            const pythonURI = importedCfg.pythonURI || window.pythonURI || '';
            const globalFetchOptions = importedCfg.fetchOptions || window.fetchOptions || {};

            const endpoint = pythonURI ? `${pythonURI}/api/match/save` : '/api/match/save';

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
                    if (data && data.profile_data && Array.isArray(data.profile_data) && data.profile_data.length > 0) {
                        // Profile exists in backend
                        loadingCheckEl.style.display = 'none';
                        existingProfilePromptEl.style.display = 'block';
                        return data.profile_data;
                    }
                } else if (response.status === 404) {
                    console.log('404 - Profile not found (expected for new users)');
                }
                
                // No profile found or error, start quiz normally
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

        let existingProfileData = null;

        loadExistingProfileBtn.onclick = () => {
            if (existingProfileData) {
                displayExistingProfile(existingProfileData);
            }
        };

        retakeFromStartBtn.onclick = () => {
            existingProfilePromptEl.style.display = 'none';
            quizEl.style.display = 'block';
            displayQuestion();
        };

        function displayExistingProfile(profileData) {
            existingProfilePromptEl.style.display = 'none';
            quizEl.style.display = 'none';
            reviewEl.style.display = 'block';

            profileDataEl.innerHTML = '';
            const allowedKeywords = ['favorite color', 'favorite animal', 'genre of music', 'favorite genre', 'favorite subject', 'subject', 'username', 'favorite band', 'band', 'musical artist', 'favorite artist'];

            const usernameResponses = [];
            const otherResponses = [];
            
            for (let resp of profileData) {
                const qLower = (resp.question || '').toLowerCase();
                const matches = allowedKeywords.some(k => qLower.includes(k));
                if (!matches) continue;

                if (qLower.includes('username')) {
                    usernameResponses.push(resp);
                } else {
                    otherResponses.push(resp);
                }
            }

            const orderedResponses = [...usernameResponses, ...otherResponses];
            for (let resp of orderedResponses) {
                const profileItem = document.createElement('div');
                profileItem.className = 'profile-item';
                const label = document.createElement('div');
                label.className = 'profile-item-label';
                label.textContent = resp.question;
                const value = document.createElement('div');
                value.className = 'profile-item-value';
                value.textContent = resp.response !== null ? resp.response : '(Not provided)';
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
            
            const userDataResponses = [];
            const startIndex = 3;
            
            for (let i = startIndex; i < questions.length; i++) {
                const q = questions[i];
                const response = q.userResponse !== undefined ? q.userResponse : null;
                userDataResponses.push({
                    question: q.question,
                    response: response,
                    type: q.allowTextEntry ? 'text' : 'multiple-choice'
                });
            }

            let leakCount = 0;
            for (let resp of userDataResponses) {
                const qLower = (resp.question || '').toLowerCase();
                const val = resp.response;
                if (val !== null && val !== undefined && String(val).trim() !== '') {
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

            profileDataEl.innerHTML = '';
            const allowedKeywords = ['favorite color', 'favorite animal', 'genre of music', 'favorite genre', 'favorite subject', 'subject', 'username', 'favorite band', 'band', 'musical artist', 'favorite artist'];

            const usernameResponses = [];
            const otherResponses = [];
            for (let resp of userDataResponses) {
                const qLower = (resp.question || '').toLowerCase();
                const matches = allowedKeywords.some(k => qLower.includes(k));
                if (!matches) continue;

                if (qLower.includes('username')) {
                    usernameResponses.push(resp);
                } else {
                    otherResponses.push(resp);
                }
            }

            const orderedResponses = [...usernameResponses, ...otherResponses];
            for (let resp of orderedResponses) {
                const profileItem = document.createElement('div');
                profileItem.className = 'profile-item';
                const label = document.createElement('div');
                label.className = 'profile-item-label';
                label.textContent = resp.question;
                const value = document.createElement('div');
                value.className = 'profile-item-value';
                value.textContent = resp.response !== null ? resp.response : '(Not provided)';
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

            // Prefer config imported by a module script, fall back to window globals
            const importedCfg = window._piiImportedConfig || {};
            const pythonURI = importedCfg.pythonURI || window.pythonURI || '';
            const globalFetchOptions = importedCfg.fetchOptions || window.fetchOptions || {};

            const endpoint = pythonURI ? `${pythonURI}/api/match/save` : '/api/match/save';

            // Merge headers but don't mutate globalFetchOptions
            const mergedHeaders = Object.assign({}, (globalFetchOptions.headers || {}), {
                'Content-Type': 'application/json'
            });

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

            // Prefer configured credentials (config.js default is 'include')
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

        // Initialize - check for existing profile first
        (async () => {
            existingProfileData = await checkExistingProfile();
        })();
    </script>
</body>
</html>