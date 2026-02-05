---
layout: opencs
title: "Microblogging Multiple Choice"
description: "Microblog Multiple Choice Quiz for Microblogging Planet"
permalink: /mcq/
parent: "AI Usage"
team: "Unzippers"
submodule: 1
author: "Krishna Visvanath"
date: 2025-10-21
---


# Submodule 1


# Learn about PII!


<html lang="en">
<head>
   <meta charset="UTF-8">
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   <title>Security Protocol Training</title>
   <style>
       :root {
           --primary-bg: #0d1117;
           --secondary-bg: #161b22;
           --tertiary-bg: #1a1a1a;
           --border-color: #30363d;
           --border-dark: #262626;
           --text-primary: #8b949e;
           --text-secondary: #6e7681;
           --text-muted: #484f58;
           --text-light: #7d8590;
           --accent-cyan: #00d9ff;
           --accent-cyan-dark: rgba(0, 217, 255, 0.15);
           --accent-green: #4caf50;
           --accent-green-light: rgba(76, 175, 80, 0.2);
           --accent-blue: #3b82f6;
           --text-light-grey: #c9d1d9;
           --font-mono: 'Courier New', monospace;
       }

       .back-button {
           display: inline-flex;
           align-items: center;
           gap: 0.5rem;
           padding: 0.5rem 1rem;
           background: var(--secondary-bg);
           border: 1px solid var(--border-color);
           border-radius: 6px;
           color: var(--text-primary);
           text-decoration: none;
           font-size: 0.9rem;
           transition: all 0.2s ease;
           margin-bottom: 1rem;
       }

       .back-button:hover {
           background: #21262d;
           border-color: var(--border-color);
           color: var(--text-light-grey);
       }

       * {
           margin: 0;
           padding: 0;
           box-sizing: border-box;
       }

       body {
           font-family: var(--font-mono);
           background: var(--primary-bg);
           color: var(--text-primary);
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
           border: 1px solid var(--border-color);
           box-shadow: 0 8px 24px rgba(0, 0, 0, 0.4);
           backdrop-filter: blur(10px);
           position: relative;
           z-index: 2;
       }

       #question {
           color: var(--text-primary);
           font-size: 1.3em;
           font-weight: 400;
           margin-bottom: 25px;
           text-shadow: 0 0 8px rgba(139, 148, 158, 0.2);
           font-family: var(--font-mono);
       }

       .options {
           display: grid;
           gap: 12px;
           margin: 20px 0;
       }

       button {
           padding: 14px 20px;
           cursor: pointer;
           border: 1px solid var(--border-color);
           border-radius: 4px;
           background: rgba(48, 54, 61, 0.2);
           color: var(--text-primary);
           font-size: 16px;
           font-weight: 400;
           transition: all 0.2s ease;
           position: relative;
           overflow: hidden;
           font-family: var(--font-mono);
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
           border-color: var(--border-color);
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

       .text-input {
           padding: 14px;
           font-size: 16px;
           border: 1px solid var(--border-color);
           border-radius: 4px;
           width: 100%;
           box-sizing: border-box;
           margin: 10px 0;
           background: rgba(13, 17, 23, 0.8);
           color: var(--text-primary);
           font-family: var(--font-mono);
       }

       .text-input:focus {
           outline: none;
           border-color: #485662;
           box-shadow: 0 0 8px rgba(72, 86, 98, 0.3);
           background: rgba(13, 17, 23, 0.95);
       }

       .text-input::placeholder {
           color: var(--text-muted);
       }

       .select-input {
           padding: 14px;
           font-size: 16px;
           border: 1px solid var(--border-color);
           border-radius: 4px;
           width: 100%;
           box-sizing: border-box;
           margin: 10px 0;
           background: rgba(13, 17, 23, 0.8);
           color: var(--text-primary);
           font-family: var(--font-mono);
           cursor: pointer;
       }

       .select-input:focus {
           outline: none;
           border-color: #485662;
           box-shadow: 0 0 8px rgba(72, 86, 98, 0.3);
           background: rgba(13, 17, 23, 0.95);
       }

       .select-input option {
           background: var(--primary-bg);
           color: var(--text-primary);
       }

       .profile-item {
           background: rgba(22, 27, 34, 0.6);
           padding: 15px;
           margin: 12px 0;
           border-radius: 4px;
           border-left: 2px solid var(--border-color);
           box-shadow: 0 2px 8px rgba(0, 0, 0, 0.2);
           position: relative;
       }

       .profile-item-label {
           font-weight: 400;
           color: var(--text-light);
           margin-bottom: 8px;
           font-size: 0.85em;
           text-transform: uppercase;
           letter-spacing: 1px;
           font-family: var(--font-mono);
       }

       .profile-item-value {
           color: var(--text-primary);
           word-break: break-word;
           font-size: 1em;
           font-family: var(--font-mono);
           display: flex;
           align-items: center;
           gap: 10px;
       }

       .profile-item-edit-btn {
           padding: 6px 12px;
           font-size: 0.85em;
           background: rgba(48, 54, 61, 0.4);
           border: 1px solid var(--border-color);
           border-radius: 4px;
           color: var(--text-primary);
           cursor: pointer;
           transition: all 0.2s ease;
           font-family: var(--font-mono);
       }

       .profile-item-edit-btn:hover {
           background: rgba(72, 86, 98, 0.4);
           border-color: #485662;
       }

       .profile-item-edit-input {
           flex: 1;
           padding: 8px;
           font-size: 1em;
           border: 1px solid #485662;
           border-radius: 4px;
           background: rgba(13, 17, 23, 0.95);
           color: var(--text-primary);
           font-family: var(--font-mono);
       }

       .profile-item-edit-actions {
           display: flex;
           gap: 8px;
       }

       .profile-item-edit-actions button {
           padding: 6px 12px;
           font-size: 0.85em;
       }

       .breather-container {
           text-align: center;
           padding: 30px;
           margin: 20px 0;
           background: rgba(22, 27, 34, 0.8);
           border-radius: 4px;
           border: 1px solid var(--border-color);
           box-shadow: 0 4px 16px rgba(0, 0, 0, 0.3);
       }

       .breather-message {
           color: var(--text-primary);
           font-size: 1.2em;
           margin-bottom: 20px;
           font-weight: 400;
           text-shadow: 0 0 8px rgba(139, 148, 158, 0.2);
           line-height: 1.6;
           font-family: var(--font-mono);
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
           border-color: var(--border-color);
           color: var(--text-muted);
       }

       @keyframes pulse {
           0%, 100% { opacity: 1; }
           50% { opacity: 0.6; }
       }

       .loading {
           animation: pulse 1.5s infinite;
       }

       /* Navigation Nodes */
       .section-nav {
           background: var(--tertiary-bg);
           border-bottom: 1px solid var(--border-dark);
           padding: 0.75rem 2rem;
           display: flex;
           gap: 0.5rem;
           justify-content: center;
           align-items: center;
           overflow-x: auto;
           scrollbar-width: none;
           flex-wrap: wrap;
       }

       .section-nav::-webkit-scrollbar {
           display: none;
       }

       .nav-node {
           width: 40px;
           height: 40px;
           border-radius: 50%;
           display: flex;
           align-items: center;
           justify-content: center;
           cursor: pointer;
           transition: all 0.3s ease;
           flex-shrink: 0;
           position: relative;
           font-size: 0.75rem;
           font-weight: 700;
           text-decoration: none;
           color: white;
           border: 2px solid;
       }

       .nav-node.locked {
           background: rgba(42, 42, 42, 0.4);
           border-color: rgba(68, 68, 68, 0.6);
           color: #71717a;
           cursor: not-allowed;
       }

       .nav-node.unlocked {
           background: var(--accent-cyan-dark);
           border-color: rgba(0, 217, 255, 0.8);
           color: var(--accent-cyan);
           box-shadow: 0 0 15px rgba(0, 217, 255, 0.3);
       }

       .nav-node.unlocked:hover {
           background: rgba(0, 217, 255, 0.25);
           transform: scale(1.1);
       }

       .nav-node.visited {
           background: var(--accent-green-light);
           border-color: rgba(102, 187, 106, 0.8);
           color: var(--accent-green);
           box-shadow: 0 0 15px rgba(76, 175, 80, 0.4);
       }

       .nav-node.current {
           background: var(--accent-blue);
           border-color: var(--accent-blue);
           color: #fff;
           box-shadow: 0 0 20px rgba(59, 130, 246, 0.6);
           transform: scale(1.15);
       }

       .nav-connector {
           width: 20px;
           height: 2px;
           background: var(--border-dark);
           flex-shrink: 0;
           transition: background 0.3s ease;
       }

       .nav-connector.visited {
           background: rgba(102, 187, 106, 0.5);
       }

       @media (max-width: 768px) {
           .section-nav {
               padding: 0.6rem 1rem;
               gap: 0.3rem;
           }

           .nav-node {
               width: 38px;
               height: 38px;
               font-size: 0.7rem;
           }

           .nav-connector {
               width: 15px;
           }
       }
   </style>
</head>
<body>
   <!-- Section Navigation -->
   <div class="section-nav" id="sectionNav">
       <a class="nav-node unlocked" href="/digitalmatchmaking/api/" data-page="1" data-url="/digitalmatchmaking/api/" title="API Blog">1</a>
       <div class="nav-connector"></div>
       <a class="nav-node locked" href="javascript:void(0)" data-page="2" data-url="/digitalmatchmaking/mcq/" title="PII Quiz">2</a>
       <div class="nav-connector"></div>
       <a class="nav-node locked" href="javascript:void(0)" data-page="3" data-url="/digitalmatchmaking/microb/" title="Microblog">3</a>
       <div class="nav-connector"></div>
       <a class="nav-node locked" href="javascript:void(0)" data-page="4" data-url="/digitalmatchmaking/bio_create/" title="Bio Creation">4</a>
       <div class="nav-connector"></div>
       <a class="nav-node locked" href="javascript:void(0)" data-page="5" data-url="/digitalmatchmaking/matchmade/" title="Matchmade">5</a>
   </div>

   <a href="/digitalmatchmaking/home/" class="back-button">← Back</a>


   <div class="quiz-container">
       <!-- PII Quiz Container - Krishna's Section -->
       <div id="loadingCheck" style="text-align: center; padding: 40px;">
           <div class="loading" style="font-size: 1.2em; color: #7d8590; font-family: 'Courier New', monospace;">
               CHECKING SYSTEM RECORDS...
           </div>
       </div>
       <div id="newUserPrompt" style="display: none;">
           <div class="breather-container">
               <div class="breather-message">NEW USER DETECTED</div>
               <p style="color: #6e7681; margin: 20px 0; font-family: 'Courier New', monospace;">
                   Would you like to fill out your profile manually or use autofill for testing?
               </p>
               <div class="breather-buttons">
                   <button id="fillManually" class="option-button">Fill Out Manually</button>
                   <button id="useAutofill" class="option-button">Use Autofill (Random)</button>
               </div>
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
           <div class="options" style="border-top: 1px solid #30363d; padding-top: 20px; margin-top: 20px;">
               <button id="saveProfile" class="option-button">Save Profile</button>
               <button id="retakeQuiz" class="option-button">Retake Assessment</button>
           </div>
           <!-- Personality Quiz Option (shown after save) -->
           <div id="personalityQuizPrompt" style="display: none; margin-top: 20px; padding-top: 20px; border-top: 1px solid #30363d;">
               <div class="breather-message" style="color: #7d8590; font-size: 1em; margin-bottom: 15px;">
                   Profile saved! Ready for the next step?
               </div>
               <button id="startPersonalityQuizBtn" class="option-button">Take Personality Quiz →</button>
           </div>
       </div>
   </div>


   <script type="module">
       import { pythonURI, fetchOptions } from '/digitalmatchmaking/assets/js/api/config.js';
       window._piiImportedConfig = window._piiImportedConfig || {};
       if (pythonURI) window._piiImportedConfig.pythonURI = pythonURI;
       if (fetchOptions) window._piiImportedConfig.fetchOptions = fetchOptions;
      
       // Autofill profile variations
       const autofillProfiles = [
           {
               "What is your favorite color?": "Red",
               "What do you want your username to be?": "ilovecompsci",
               "What's your favorite animal?": "Dogs",
               "What is your favorite genre of music?": "Rock",
               "What is your favorite band/musical artist?": "Radiohead",
               "What is your favorite subject?": "English"
           },
           {
               "What is your favorite color?": "Blue",
               "What do you want your username to be?": "codingwizard42",
               "What's your favorite animal?": "Cats",
               "What is your favorite genre of music?": "Pop",
               "What is your favorite band/musical artist?": "Taylor Swift",
               "What is your favorite subject?": "Math"
           },
           {
               "What is your favorite color?": "Green",
               "What do you want your username to be?": "techsavvy2025",
               "What's your favorite animal?": "Birds",
               "What is your favorite genre of music?": "Rap",
               "What is your favorite band/musical artist?": "Kendrick Lamar",
               "What is your favorite subject?": "Science"
           },
           {
               "What is your favorite color?": "Purple",
               "What do you want your username to be?": "datanerd101",
               "What's your favorite animal?": "Fish",
               "What is your favorite genre of music?": "Rock",
               "What is your favorite band/musical artist?": "The Beatles",
               "What is your favorite subject?": "History"
           }
       ];
      
       function getRandomAutofillProfile() {
           const randomIndex = Math.floor(Math.random() * autofillProfiles.length);
           return autofillProfiles[randomIndex];
       }
      
       function applyAutofill() {
           const autofillData = getRandomAutofillProfile();
           console.log('Applying autofill with profile:', autofillData);
          
           // Store in session storage
           const userDataJSON = JSON.stringify(autofillData, null, 2);
           sessionStorage.setItem('userQuizResponses', userDataJSON);
           window.userQuizData = userDataJSON;
          
           // Display the autofilled profile
           displayProfileData(autofillData);
          
           // Show review section
           loadingCheckEl.style.display = 'none';
           newUserPromptEl.style.display = 'none';
           existingProfilePromptEl.style.display = 'none';
           quizEl.style.display = 'none';
           reviewEl.style.display = 'block';
       }
      
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
       const newUserPromptEl = document.getElementById('newUserPrompt');
       const existingProfilePromptEl = document.getElementById('existingProfilePrompt');
       const loadExistingProfileBtn = document.getElementById('loadExistingProfile');
       const retakeFromStartBtn = document.getElementById('retakeFromStart');
       const fillManuallyBtn = document.getElementById('fillManually');
       const useAutofillBtn = document.getElementById('useAutofill');


       let existingProfileData = null;
       let editingProfileData = {}; // Track current profile data being edited

       // Function to get question options (for dropdowns and multiple choice)
       function getQuestionOptions(questionText) {
           const question = questions.find(q => q.question === questionText);
           return question ? question.options : null;
       }

       // Function to display profile data with edit buttons
       function displayProfileData(profileData) {
           profileDataEl.innerHTML = '';
           editingProfileData = {...profileData}; // Make a copy for editing
          
           for (let [question, response] of Object.entries(profileData)) {
               const profileItem = document.createElement('div');
               profileItem.className = 'profile-item';
               profileItem.dataset.question = question;
               
               const label = document.createElement('div');
               label.className = 'profile-item-label';
               label.textContent = question;
               
               const valueContainer = document.createElement('div');
               valueContainer.className = 'profile-item-value';
               
               const value = document.createElement('span');
               value.textContent = response;
               value.className = 'profile-value-text';
               
               const editBtn = document.createElement('button');
               editBtn.className = 'profile-item-edit-btn';
               editBtn.textContent = 'Edit';
               editBtn.onclick = () => enableEditMode(profileItem, question, response);
               
               valueContainer.appendChild(value);
               valueContainer.appendChild(editBtn);
               profileItem.appendChild(label);
               profileItem.appendChild(valueContainer);
               profileDataEl.appendChild(profileItem);
           }
       }

       // Function to enable edit mode for a profile item
       function enableEditMode(profileItem, question, currentValue) {
           const valueContainer = profileItem.querySelector('.profile-item-value');
           valueContainer.innerHTML = '';
           
           const questionOptions = getQuestionOptions(question);
           let inputElement;
           
           if (questionOptions) {
               // Create dropdown for questions with options
               inputElement = document.createElement('select');
               inputElement.className = 'profile-item-edit-input select-input';
               
               questionOptions.forEach((option) => {
                   const optionEl = document.createElement('option');
                   optionEl.value = option;
                   optionEl.textContent = option;
                   if (option === currentValue) {
                       optionEl.selected = true;
                   }
                   inputElement.appendChild(optionEl);
               });
           } else {
               // Create text input for free text questions
               inputElement = document.createElement('input');
               inputElement.type = 'text';
               inputElement.className = 'profile-item-edit-input';
               inputElement.value = currentValue;
           }
           
           const actionsContainer = document.createElement('div');
           actionsContainer.className = 'profile-item-edit-actions';
           
           const saveBtn = document.createElement('button');
           saveBtn.textContent = 'Save';
           saveBtn.onclick = () => saveEdit(profileItem, question, inputElement.value);
           
           const cancelBtn = document.createElement('button');
           cancelBtn.textContent = 'Cancel';
           cancelBtn.onclick = () => cancelEdit(profileItem, question, currentValue);
           
           actionsContainer.appendChild(saveBtn);
           actionsContainer.appendChild(cancelBtn);
           
           valueContainer.appendChild(inputElement);
           valueContainer.appendChild(actionsContainer);
           
           inputElement.focus();
       }

       // Function to save an edit
       function saveEdit(profileItem, question, newValue) {
           if (!newValue || newValue.trim() === '') {
               alert('Please enter a value');
               return;
           }
           
           // Update the editing profile data
           editingProfileData[question] = newValue;
           
           // Update session storage
           sessionStorage.setItem('userQuizResponses', JSON.stringify(editingProfileData));
           window.userQuizData = JSON.stringify(editingProfileData, null, 2);
           
           // Refresh the display
           displayProfileData(editingProfileData);
       }

       // Function to cancel an edit
       function cancelEdit(profileItem, question, originalValue) {
           // Refresh the display to show original value
           displayProfileData(editingProfileData);
       }


       async function checkExistingProfile() {
           const importedCfg = window._piiImportedConfig || {};
           const pythonURI = importedCfg.pythonURI || window.pythonURI || '';
           const globalFetchOptions = importedCfg.fetchOptions || window.fetchOptions || {};


           // Use /api/match/data which has GET method working
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
              
               // Handle 404 - no profile exists yet
               if (response.status === 404) {
                   console.log('404 - Profile not found (expected for new users)');
                   loadingCheckEl.style.display = 'none';
                   newUserPromptEl.style.display = 'block';
                   return null;
               }
               
               // Handle other non-OK responses
               if (!response.ok) {
                   console.log(`Non-OK status code: ${response.status}`);
                   loadingCheckEl.style.display = 'none';
                   newUserPromptEl.style.display = 'block';
                   return null;
               }
              
               // Parse the response
               const responseText = await response.text();
               console.log('Response body (raw):', responseText);
               
               let data;
               try {
                   data = JSON.parse(responseText);
               } catch (parseErr) {
                   console.error('Failed to parse response as JSON:', parseErr);
                   loadingCheckEl.style.display = 'none';
                   newUserPromptEl.style.display = 'block';
                   return null;
               }
              
               console.log('Parsed response data:', data);
               console.log('Type of data:', typeof data);
               
               // The /data endpoint returns: { message: "...", data: { profile: {...}, ...} }
               // We need to extract profile_quiz from data.data.profile.profile_quiz
               const profileData = data.data && data.data.profile ? data.data.profile : null;
               console.log('profileData:', profileData);
               
               if (profileData && profileData.profile_quiz) {
                   const profile_quiz = profileData.profile_quiz;
                   console.log('profile_quiz:', profile_quiz);
                   console.log('Type of profile_quiz:', typeof profile_quiz);
                   console.log('Keys in profile_quiz:', Object.keys(profile_quiz));
                   console.log('Number of keys:', Object.keys(profile_quiz).length);
                   
                   // Check if profile_quiz has actual data
                   if (typeof profile_quiz === 'object' && Object.keys(profile_quiz).length > 0) {
                       // Store the profile data
                       existingProfileData = profile_quiz;
                       console.log('✅ PROFILE FOUND! Stored existing profile data:', existingProfileData);
                       console.log('Hiding loading, showing existing profile prompt...');
                      
                       loadingCheckEl.style.display = 'none';
                       existingProfilePromptEl.style.display = 'block';
                       console.log('loadingCheckEl display:', loadingCheckEl.style.display);
                       console.log('existingProfilePromptEl display:', existingProfilePromptEl.style.display);
                       return profile_quiz;
                   }
               }
               
               // If we get here, profile_quiz is null, undefined, or empty
               console.log('❌ Profile quiz not found or empty');
               
               loadingCheckEl.style.display = 'none';
               newUserPromptEl.style.display = 'block';
               return null;
               
           } catch (err) {
               console.error('Error checking profile:', err);
               console.error('Error stack:', err.stack);
               console.log('Error occurred, showing new user prompt');
               loadingCheckEl.style.display = 'none';
               newUserPromptEl.style.display = 'block';
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


       fillManuallyBtn.onclick = () => {
           console.log('User chose to fill manually');
           newUserPromptEl.style.display = 'none';
           quizEl.style.display = 'block';
           currentQuestion = 0;
           score = 0;
           selectedOption = null;
           displayQuestion();
       };


       useAutofillBtn.onclick = () => {
           console.log('User chose autofill');
           applyAutofill();
       };


       function displayExistingProfile(profileData) {
           existingProfilePromptEl.style.display = 'none';
           quizEl.style.display = 'none';
           reviewEl.style.display = 'block';

           displayProfileData(profileData);
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


           // Display profile data with edit buttons
           displayProfileData(userDataResponses);
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
           // Use editingProfileData instead of session storage, as it has the latest edits
           const profileData = editingProfileData;
           
           if (!profileData || Object.keys(profileData).length === 0) {
               alert("No profile data found to save.");
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
               alert("Profile saved successfully!");


               // Show the personality quiz prompt after successful save
               const personalityPrompt = document.getElementById('personalityQuizPrompt');
               if (personalityPrompt) {
                   personalityPrompt.style.display = 'block';
               }


               // Hide the save button since it's done
               saveProfileBtn.style.display = 'none';
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


       /* ========== PERSONALITY QUIZ (KRISHNA'S SECTION) ========== */


       // Personality quiz elements
       const personalityQuizSection = document.createElement('div');
       personalityQuizSection.id = 'personalityQuizSection';
       personalityQuizSection.style.display = 'none';


       // Personality quiz questions
       const personalityQuestions = [
           {
               id: 1,
               question: "At a social gathering, you typically...",
               options: [
                   { text: "Seek out new people and enjoy being the center of attention", value: "E_high" },
                   { text: "Talk to a few close friends and enjoy smaller conversations", value: "I_moderate" },
                   { text: "Prefer observing and only engage when approached", value: "I_high" },
                   { text: "Mix between groups and one-on-one conversations", value: "E_moderate" }
               ]
           },
           {
               id: 2,
               question: "When making important decisions, you rely most on...",
               options: [
                   { text: "Logic, facts, and objective analysis", value: "T_high" },
                   { text: "How it will affect people and relationships", value: "F_high" },
                   { text: "A balance of logic and emotional impact", value: "T_moderate" },
                   { text: "Gut feeling and personal values", value: "F_moderate" }
               ]
           },
           {
               id: 3,
               question: "Your ideal weekend involves...",
               options: [
                   { text: "Spontaneous adventures and seeing where the day takes you", value: "P_high" },
                   { text: "A well-planned itinerary of activities", value: "J_high" },
                   { text: "A loose plan with room for flexibility", value: "P_moderate" },
                   { text: "Structured activities with some downtime built in", value: "J_moderate" }
               ]
           },
           {
               id: 4,
               question: "When learning something new, you prefer...",
               options: [
                   { text: "Understanding the big picture and future possibilities", value: "N_high" },
                   { text: "Hands-on practice with concrete examples", value: "S_high" },
                   { text: "Starting with theory, then applying it practically", value: "N_moderate" },
                   { text: "Step-by-step instructions with clear outcomes", value: "S_moderate" }
               ]
           },
           {
               id: 5,
               question: "Your ideal date or hangout would be...",
               options: [
                   { text: "An exciting adventure like hiking, exploring, or trying something new", value: "E_high" },
                   { text: "A cozy night in with movies, games, or deep conversations", value: "I_high" },
                   { text: "A nice dinner or coffee shop where you can talk and connect", value: "E_moderate" },
                   { text: "Something creative like a museum, concert, or art class", value: "N_high" }
               ]
           },
           {
               id: 6,
               question: "After a long day, you recharge by...",
               options: [
                   { text: "Being alone with your thoughts or hobbies", value: "I_high" },
                   { text: "Calling friends or going out", value: "E_high" },
                   { text: "Quiet time first, then maybe socializing", value: "I_moderate" },
                   { text: "Light social interaction with close ones", value: "E_moderate" }
               ]
           },
           {
               id: 7,
               question: "When someone shares a problem with you, you typically...",
               options: [
                   { text: "Offer solutions and practical advice", value: "T_high" },
                   { text: "Listen empathetically and validate their feelings", value: "F_high" },
                   { text: "Ask questions to understand before responding", value: "T_moderate" },
                   { text: "Share similar experiences to show understanding", value: "F_moderate" }
               ]
           },
           {
               id: 8,
               question: "What's something you're passionate about?",
               options: [
                   { text: "Creative pursuits like art, music, or writing", value: "N_high" },
                   { text: "Helping others and making a positive difference", value: "F_high" },
                   { text: "Learning new things and solving problems", value: "T_high" },
                   { text: "Sports, fitness, or outdoor adventures", value: "S_high" }
               ]
           },
           {
               id: 9,
               question: "When planning a trip, you...",
               options: [
                   { text: "Research extensively and create detailed plans", value: "J_high" },
                   { text: "Book tickets and figure out the rest as you go", value: "P_high" },
                   { text: "Plan key activities but leave room for spontaneity", value: "P_moderate" },
                   { text: "Follow recommended itineraries from others", value: "S_moderate" }
               ]
           },
           {
               id: 10,
               question: "In conversations, you tend to focus on...",
               options: [
                   { text: "Abstract ideas, theories, and what could be", value: "N_high" },
                   { text: "Concrete facts, experiences, and what is", value: "S_high" },
                   { text: "Both practical details and underlying meanings", value: "N_moderate" },
                   { text: "Real-world applications and examples", value: "S_moderate" }
               ]
           },
           {
               id: 11,
               question: "When facing conflict, you're more likely to...",
               options: [
                   { text: "Address it directly with facts and logic", value: "T_high" },
                   { text: "Consider feelings and find a harmonious solution", value: "F_high" },
                   { text: "Avoid it unless absolutely necessary", value: "I_high" },
                   { text: "Seek mediation or a third-party perspective", value: "F_moderate" }
               ]
           },
           {
               id: 12,
               question: "If you could change one thing about the world, what would it be?",
               options: [
                   { text: "End poverty and inequality for everyone", value: "F_high" },
                   { text: "Protect the environment and fight climate change", value: "N_high" },
                   { text: "Improve education and access to knowledge", value: "T_high" },
                   { text: "Bring people together and reduce conflict", value: "F_moderate" }
               ]
           },
           {
               id: 13,
               question: "Your approach to rules and deadlines is...",
               options: [
                   { text: "Strict - rules exist for a reason and should be followed", value: "J_high" },
                   { text: "Flexible - guidelines that can bend based on context", value: "P_high" },
                   { text: "Respectful but willing to question when needed", value: "P_moderate" },
                   { text: "Depends on whether they make logical sense", value: "T_moderate" }
               ]
           }
       ];


       let currentPersonalityQuestion = 0;
       let personalityAnswers = {};


       function startPersonalityQuiz() {
           // Hide review section and show personality quiz
           reviewEl.style.display = 'none';
           const quizContainer = document.querySelector('.quiz-container');


           // Create personality quiz UI
           personalityQuizSection.innerHTML = `
               <div class="breather-container">
                   <div class="breather-message">PERSONALITY ASSESSMENT</div>
                   <p style="color: #6e7681; margin: 20px 0; font-family: 'Courier New', monospace;">
                       Now let's understand your personality traits for better matchmaking
                   </p>
               </div>
               <div id="personalityQuizContent" style="margin-top: 20px;">
                   <div id="personalityQuestion"></div>
                   <div class="options" id="personalityOptions"></div>
                   <button id="personalitySubmit" type="button">Submit Answer</button>
               </div>
           `;


           quizContainer.appendChild(personalityQuizSection);
           personalityQuizSection.style.display = 'block';


           currentPersonalityQuestion = 0;
           personalityAnswers = {};
           displayPersonalityQuestion();
       }


       function displayPersonalityQuestion() {
           const question = personalityQuestions[currentPersonalityQuestion];
           const questionEl = document.getElementById('personalityQuestion');
           const optionsEl = document.getElementById('personalityOptions');
           const submitBtn = document.getElementById('personalitySubmit');


           questionEl.textContent = `Question ${currentPersonalityQuestion + 1}/${personalityQuestions.length}: ${question.question}`;
           questionEl.style.color = '#8b949e';
           questionEl.style.fontSize = '1.1em';
           questionEl.style.marginBottom = '20px';


           optionsEl.innerHTML = '';


           if (question.type === 'freeResponse') {
               const textInput = document.createElement('textarea');
               textInput.className = 'text-input';
               textInput.placeholder = question.placeholder;
               textInput.rows = 4;
               textInput.style.resize = 'vertical';
               textInput.value = personalityAnswers[question.id] || '';
               textInput.oninput = () => {
                   submitBtn.disabled = textInput.value.trim().length < 3;
               };
               optionsEl.appendChild(textInput);
               submitBtn.disabled = textInput.value.trim().length < 3;
               question.textInputElement = textInput;
           } else {
               question.options.forEach((option, index) => {
                   const button = document.createElement('button');
                   button.className = 'option-button';
                   button.textContent = option.text;
                   button.onclick = () => selectPersonalityOption(question.id, option.value, button);
                   if (personalityAnswers[question.id] === option.value) {
                       button.classList.add('selected');
                   }
                   optionsEl.appendChild(button);
               });
               submitBtn.disabled = !personalityAnswers[question.id];
           }
       }


       function selectPersonalityOption(questionId, value, element) {
           personalityAnswers[questionId] = value;


           const buttons = document.querySelectorAll('#personalityOptions .option-button');
           buttons.forEach(btn => btn.classList.remove('selected'));
           element.classList.add('selected');


           document.getElementById('personalitySubmit').disabled = false;
       }


       function submitPersonalityAnswer() {
           const question = personalityQuestions[currentPersonalityQuestion];


           if (question.type === 'freeResponse') {
               const textInput = question.textInputElement;
               if (textInput && textInput.value.trim().length >= 3) {
                   personalityAnswers[question.id] = textInput.value.trim();
               } else {
                   alert('Please write at least a few words before continuing');
                   return;
               }
           } else {
               if (!personalityAnswers[question.id]) {
                   alert('Please select an answer');
                   return;
               }
           }


           currentPersonalityQuestion++;
           if (currentPersonalityQuestion < personalityQuestions.length) {
               displayPersonalityQuestion();
           } else {
               completePersonalityQuiz();
           }
       }


       async function savePersonalityToBackend(personalityData) {
           const importedCfg = window._piiImportedConfig || {};
           const pythonURI = importedCfg.pythonURI || window.pythonURI || '';
           const globalFetchOptions = importedCfg.fetchOptions || window.fetchOptions || {};


           const endpoint = pythonURI ? `${pythonURI}/api/match/save` : '/api/match/save';


           const mergedHeaders = Object.assign({}, (globalFetchOptions.headers || {}), {
               'Content-Type': 'application/json'
           });


           const payload = { profile_data: { personality_quiz: personalityData } };


           console.log('=== SAVE PERSONALITY QUIZ DEBUG ===');
           console.log('Saving personality quiz to:', endpoint);
           console.log('Payload:', payload);


           const options = Object.assign({}, globalFetchOptions, {
               method: 'POST',
               headers: mergedHeaders,
               body: JSON.stringify(payload)
           });


           if (!options.credentials) options.credentials = 'include';


           try {
               const response = await fetch(endpoint, options);
               console.log('Personality save response status:', response.status);


               if (!response.ok) {
                   console.error('Failed to save personality quiz:', response.status);
                   return false;
               }


               const data = await response.json();
               console.log('Personality quiz saved successfully:', data);
               return true;
           } catch (err) {
               console.error('Error saving personality quiz:', err);
               return false;
           }
       }


       async function completePersonalityQuiz() {
           // Save personality quiz responses to sessionStorage
           sessionStorage.setItem('personalityQuizResponses', JSON.stringify(personalityAnswers));


           // Save personality quiz to backend
           await savePersonalityToBackend(personalityAnswers);


           // Show completion message
           document.getElementById('personalityQuizContent').innerHTML = `
               <div class="breather-container">
                   <div class="breather-message" style="color: #4caf50;">✅ PERSONALITY ASSESSMENT COMPLETE</div>
                   <p style="color: #6e7681; margin: 20px 0; font-family: 'Courier New', monospace;">
                       Assessment complete! Ready for AI personality analysis.
                   </p>
                   <div class="breather-buttons">
                       <button id="goToAIAnalysis" class="option-button">View AI Analysis →</button>
                       <button id="retakePersonality" class="option-button">Retake Personality Quiz</button>
                   </div>
               </div>
           `;


           document.getElementById('goToAIAnalysis').onclick = () => {
               window.location.href = '/digitalmatchmaking/microb/';
           };


           document.getElementById('retakePersonality').onclick = () => {
               startPersonalityQuiz();
           };
       }


       // Attach personality quiz submit handler
       document.addEventListener('click', (e) => {
           if (e.target && e.target.id === 'personalitySubmit') {
               submitPersonalityAnswer();
           }
       });


       /* ========== INITIALIZE PROFILE QUIZ ON PAGE LOAD ========== */
       
       // Automatically start checking for existing profile when page loads
       window.addEventListener('DOMContentLoaded', async () => {
           console.log('Profile quiz initializing...');


           // Set up personality quiz button handler
           const startPersonalityQuizBtn = document.getElementById('startPersonalityQuizBtn');
           if (startPersonalityQuizBtn) {
               startPersonalityQuizBtn.onclick = () => {
                   console.log('Starting personality quiz...');
                   startPersonalityQuiz();
               };
           }


           await checkExistingProfile();

           // Page Navigation System
           const VISITED_KEY = 'api_visited_pages';
           let visitedPages = {};

           const pages = [
               { id: 1, url: '/digitalmatchmaking/api/' },
               { id: 2, url: '/digitalmatchmaking/mcq/' },
               { id: 3, url: '/digitalmatchmaking/microb/' },
               { id: 4, url: '/digitalmatchmaking/bio_create/' },
               { id: 5, url: '/digitalmatchmaking/matchmade/' }
           ];

           function loadVisitedPages() {
               try {
                   return JSON.parse(localStorage.getItem(VISITED_KEY)) || {};
               } catch (e) {
                   return {};
               }
           }

           function saveVisitedPages() {
               try {
                   localStorage.setItem(VISITED_KEY, JSON.stringify(visitedPages));
               } catch (e) {}
           }

           function isPageUnlocked(pageId) {
               if (pageId === 1) return true;
               // Page 2 is always unlocked (this is the current page)
               if (pageId === 2) return true;
               // Other pages require previous page to be visited
               return visitedPages[pageId - 1];
           }

           function markPageVisited(pageId) {
               visitedPages[pageId] = true;
               saveVisitedPages();
               updateNavigation();
           }

           function updateNavigation() {
               const navNodes = document.querySelectorAll('.nav-node');
               const navConnectors = document.querySelectorAll('.nav-connector');
               
               navNodes.forEach((node, idx) => {
                   const pageId = idx + 1;
                   node.classList.remove('locked', 'unlocked', 'visited', 'current');
                   
                   if (visitedPages[pageId]) {
                       node.classList.add('visited');
                       node.href = node.dataset.url;
                       node.style.cursor = 'pointer';
                       node.onclick = function() {
                           window.location.href = this.dataset.url;
                       };
                   } else if (isPageUnlocked(pageId)) {
                       node.classList.add('unlocked');
                       node.href = node.dataset.url;
                       node.style.cursor = 'pointer';
                       node.onclick = function() {
                           markPageVisited(pageId);
                           window.location.href = this.dataset.url;
                       };
                   } else {
                       node.classList.add('locked');
                       node.style.cursor = 'not-allowed';
                       node.href = 'javascript:void(0)';
                       node.onclick = null;
                   }
               });

               // Update connectors
               navConnectors.forEach((conn, idx) => {
                   if (visitedPages[idx + 1]) {
                       conn.classList.add('visited');
                   } else {
                       conn.classList.remove('visited');
                   }
               });

               // Highlight current page
               const currentUrl = window.location.pathname;
               navNodes.forEach((node, idx) => {
                   if (node.dataset.url === currentUrl) {
                       node.classList.add('current');
                   }
               });
           }

           // Initialize navigation on page load
           visitedPages = loadVisitedPages();
           
           // Mark current page as visited
           const currentUrl = window.location.pathname;
           pages.forEach((page, idx) => {
               if (page.url === currentUrl) {
                   markPageVisited(page.id);
               }
           });

           updateNavigation();
       });
   </script>
</body>
</html>