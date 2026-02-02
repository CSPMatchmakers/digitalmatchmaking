---
layout: post
title: "Personality Matchmaking Quiz"
description: "Discover your personality type for better connections"
permalink: /microb/
submodule: 4
categories: [CSP, Submodule, Microblogging]
tags: [matchmaking, personality, quiz, submodule]
author: "Nicolas Diaz"
breadcrumb: true
---
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Personality Matchmaking Quiz</title>




<style>
.back-button {
   display: inline-flex;
   align-items: center;
   gap: 0.5rem;
   padding: 0.4rem 0.8rem;
   background: #161b22;
   border: 1px solid #30363d;
   border-radius: 6px;
   color: #8b949e;
   text-decoration: none;
   font-size: 0.85rem;
   transition: all 0.2s ease;
   margin-bottom: 0.5rem;
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
   background: #0d1117 !important;
   color: #8b949e;
   padding: 12px 20px;
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


h1, h2, h3 {
   margin: 0;
   color: #8b949e;
   font-family: 'Courier New', monospace;
}


/* ---------- HEADER ---------- */
header {
   text-align: center;
   margin-bottom: 16px;
}


/* ---------- CONTAINER ---------- */
.container {
   position: relative;
   width: 100%;
   max-width: 800px;
   margin: 0 auto;
   display: flex;
   flex-direction: column;
   align-items: center;
   gap: 12px;
   padding: 0 16px;
   z-index: 2;
}


/* ---------- INFO CARDS (Terminal Style) ---------- */
.info-card {
   background: rgba(22, 27, 34, 0.85) !important;
   border: 1px solid #30363d !important;
   border-radius: 6px !important;
   padding: 20px !important;
   width: 100%;
   max-width: 800px;
   text-align: center;
   cursor: default;
   transition: all 0.2s ease;
   position: relative;
   box-shadow: 0 8px 24px rgba(0, 0, 0, 0.4) !important;
   backdrop-filter: blur(10px);
}


.info-card:hover {
   border-color: #485662 !important;
   box-shadow: 0 0 10px rgba(100, 120, 130, 0.2) !important;
}


.info-card h3 {
   color: #8b949e;
   margin-bottom: 12px;
   font-size: 1.3em;
   font-weight: 400;
   text-shadow: 0 0 8px rgba(139, 148, 158, 0.2);
   font-family: 'Courier New', monospace;
}


.info-card p {
   color: #6e7681;
   font-size: 14px;
   line-height: 1.6;
   font-family: 'Courier New', monospace;
}


/* ---------- FORM STYLING (Terminal Style) ---------- */
label {
   margin-top: 16px;
   display: block;
   font-weight: 400;
   color: #7d8590;
   font-size: 0.85em;
   text-align: left;
   text-transform: uppercase;
   letter-spacing: 1px;
   font-family: 'Courier New', monospace;
}


select, input {
   width: 100%;
   margin-top: 8px;
   padding: 14px;
   background: rgba(13, 17, 23, 0.8);
   border-radius: 4px;
   border: 1px solid #30363d;
   color: #8b949e;
   font-size: 16px;
   transition: all 0.2s ease;
   font-family: 'Courier New', monospace;
}


select:focus, input:focus {
   outline: none;
   border-color: #485662;
   box-shadow: 0 0 8px rgba(72, 86, 98, 0.3);
   background: rgba(13, 17, 23, 0.95);
}


select:hover, input:hover {
   border-color: #485662;
}


select option {
   background: #0d1117;
   color: #8b949e;
}


input::placeholder {
   color: #484f58;
}


/* ---------- BUTTON (Terminal Style) ---------- */
button {
   margin-top: 14px;
   padding: 14px 20px;
   width: 100%;
   border-radius: 4px;
   border: 1px solid #30363d;
   background: rgba(48, 54, 61, 0.3);
   color: #8b949e;
   font-size: 16px;
   font-weight: 400;
   cursor: pointer;
   transition: all 0.2s ease;
   text-transform: uppercase;
   letter-spacing: 2px;
   font-family: 'Courier New', monospace;
   position: relative;
   overflow: hidden;
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


button:hover:not(:disabled) {
   background: rgba(48, 54, 61, 0.5);
   border-color: #485662;
   box-shadow: 0 0 10px rgba(100, 120, 130, 0.2);
}


button:disabled {
   opacity: 0.4;
   cursor: not-allowed;
}


/* ---------- RESULT BOX ---------- */
#result-box {
   text-align: center;
}


#server-status {
   color: #8b949e;
   margin-bottom: 16px;
   font-weight: 400;
   font-size: 14px;
   padding: 10px;
   border-radius: 4px;
   background: rgba(48, 54, 61, 0.3);
   font-family: 'Courier New', monospace;
}


/* ---------- PROFILE DISPLAY ---------- */
#profile-display {
   text-align: left;
}


#profile-display h3 {
   color: #8b949e;
   font-size: 1em;
   margin-bottom: 12px;
   text-align: center;
}


#profile-display h4 {
   color: #7d8590;
   font-size: 0.9em;
   margin: 12px 0 8px 0;
   font-family: 'Courier New', monospace;
}


#profile-display > div {
   background: rgba(22, 27, 34, 0.6) !important;
   padding: 12px !important;
   margin-bottom: 10px !important;
   border-radius: 4px !important;
   border-left: 2px solid #30363d !important;
}


#profile-display p {
   font-size: 13px;
   line-height: 1.5;
   margin: 6px 0;
}


/* ---------- LOADING ANIMATION ---------- */
.loading-dots {
   display: inline-block;
}


.loading-dots::after {
   content: '';
   animation: dots 1.5s steps(4, end) infinite;
}


@keyframes dots {
   0%, 20% { content: ''; }
   40% { content: '.'; }
   60% { content: '..'; }
   80%, 100% { content: '...'; }
}


@keyframes pulse {
   0%, 100% { opacity: 1; }
   50% { opacity: 0.6; }
}


.loading {
   animation: pulse 1.5s infinite;
}


/* ---------- SCROLLBAR STYLING ---------- */
::-webkit-scrollbar {
   width: 6px;
}


::-webkit-scrollbar-track {
   background: #0d1117;
}


::-webkit-scrollbar-thumb {
   background: #30363d;
   border-radius: 3px;
}


::-webkit-scrollbar-thumb:hover {
   background: #485662;
}


/* ---------- RESPONSIVE DESIGN ---------- */
@media (max-width: 768px) {
   .container {
       padding: 0 12px;
   }


   .info-card {
       padding: 16px !important;
   }


   button {
       padding: 12px 16px;
       font-size: 14px;
   }
}
</style>
</head>




<body>




<a href="/digitalmatchmaking/home/" class="back-button">← Back</a>




<header>
<h1 style="font-size: 1.8em; font-weight: 600; margin-bottom: 4px; color: #c9d1d9;">💕 Find Your Perfect Match</h1>
<p style="color: #8b949e; font-size: 14px; margin: 0;">Discover your unique personality type</p>
</header>




<!-- ---------- AI ANALYSIS INPUT ---------- -->
<div class="container">
<div class="info-card">
  <h3>AI PERSONALITY ANALYSIS</h3>


  <!-- Input Section (hidden after generating) -->
  <div id="input-section">
    <p style="margin-bottom: 16px;">
      Customize your AI analysis based on both your profile and personality quiz results
    </p>


    <label for="analysis-focus">Analysis Focus</label>
    <select id="analysis-focus">
      <option value="">Select focus area...</option>
      <option value="compatibility">Relationship Compatibility Insights</option>
      <option value="strengths">Personal Strengths & Growth Areas</option>
      <option value="communication">Communication Style Analysis</option>
      <option value="comprehensive">Comprehensive Analysis (All Above)</option>
    </select>


    <label for="analysis-depth">Detail Level</label>
    <select id="analysis-depth">
      <option value="">Select detail level...</option>
      <option value="brief">Brief Overview (Key Points Only)</option>
      <option value="moderate">Moderate Detail (Balanced)</option>
      <option value="deep">Deep Dive (Comprehensive Analysis)</option>
    </select>


    <button id="generate-analysis-btn" onclick="generateAIAnalysis()" disabled>
      Generate AI Analysis
    </button>
  </div>


  <!-- Result Display (replaces input section) -->
  <div id="result-box" style="display:none;">
    <p id="server-status"></p>
    <div id="profile-display"></div>
    <button id="regenerate-btn" onclick="showInputSection()" style="margin-top: 20px;">
      ← Generate New Analysis
    </button>
  </div>
</div>
</div>




<script type="module">
import { pythonURI } from '{{site.baseurl}}/assets/js/api/config.js';




/* ========== CHECK FOR QUIZ COMPLETION ========== */




/**
* Check if both quizzes have been completed
*/
function checkQuizzesCompleted() {
console.log('🔍 Checking if both quizzes are completed...');


// Check sessionStorage for personality quiz
const personalityData = sessionStorage.getItem('personalityQuizResponses');


// Check sessionStorage for profile quiz
const profileData = sessionStorage.getItem('userQuizResponses');


console.log('Personality quiz data:', personalityData ? 'Found' : 'Not found');
console.log('Profile quiz data:', profileData ? 'Found' : 'Not found');


if (!personalityData || !profileData) {
  // Redirect back to Krishna's quiz page if not completed
  alert('⚠️ Please complete both the profile quiz and personality quiz on Krishna\'s page first!');
  window.location.href = '/digitalmatchmaking/mcq/';
  return false;
}


return true;
}




/**
* Enable analysis button when both dropdowns are selected
*/
function updateAnalysisButton() {
const focusSelect = document.getElementById('analysis-focus');
const depthSelect = document.getElementById('analysis-depth');
const generateBtn = document.getElementById('generate-analysis-btn');


if (focusSelect.value && depthSelect.value) {
  generateBtn.disabled = false;
} else {
  generateBtn.disabled = true;
}
}




/**
* Main function to generate AI analysis
*/
/**
* Show input section and hide results
*/
function showInputSection() {
document.getElementById("input-section").style.display = "block";
document.getElementById("result-box").style.display = "none";
}


async function generateAIAnalysis() {
const focusSelect = document.getElementById('analysis-focus');
const depthSelect = document.getElementById('analysis-depth');


const focus = focusSelect.value;
const depth = depthSelect.value;


if (!focus || !depth) {
  alert('Please select both focus area and detail level');
  return;
}


// Hide input section, show result box with loading state
document.getElementById("input-section").style.display = "none";
document.getElementById("result-box").style.display = "block";
document.getElementById("server-status").innerHTML = '⏳ Generating AI analysis<span class="loading-dots"></span>';
document.getElementById("profile-display").innerHTML = '';


// Fetch both quiz datasets (INPUT)
const profileData = await fetchUserProfile();
const personalityData = fetchPersonalityQuizData();


console.log('📊 Profile data:', profileData);
console.log('🧠 Personality data:', personalityData);


// Generate comprehensive AI analysis (PROCEDURE with DIFFERENT INPUTS)
const analysis = await generateComprehensiveAnalysis(profileData, personalityData, focus, depth);


// Display the analysis (OUTPUT)
setTimeout(async () => {
  displayComprehensiveAnalysis(analysis, profileData, personalityData);


  // Save analysis to backend for matchmaking
  const saved = await saveAnalysisToBackend(analysis, personalityData);
  if (saved) {
    document.getElementById("server-status").textContent = "✅ Analysis saved! You're ready for matchmaking!";
  } else {
    document.getElementById("server-status").textContent = "✅ Your AI analysis is ready! (Save failed)";
  }
}, 500);
}




/* ========== FETCH BOTH QUIZ DATASETS (INPUT) ========== */


/**
* Fetch user's profile data from Krishna's quiz (backend)
*/
async function fetchUserProfile() {
try {
  const response = await fetch(`${pythonURI}/api/match/save`, {
    method: 'GET',
    credentials: 'include',
    headers: { 'Content-Type': 'application/json' }
  });


  console.log('📊 Fetching profile from backend...');


  if (!response.ok) {
    console.log('⚠️ No profile found in backend, checking sessionStorage');
    const sessionProfile = sessionStorage.getItem('userQuizResponses');
    if (sessionProfile) {
      return JSON.parse(sessionProfile);
    }
    return generateSampleProfile();
  }


  const data = await response.json();
  console.log('✅ Profile fetched from backend:', data);


  if (data && data.profile_quiz) {
    return data.profile_quiz;
  } else {
    // Fallback to sessionStorage
    const sessionProfile = sessionStorage.getItem('userQuizResponses');
    if (sessionProfile) {
      return JSON.parse(sessionProfile);
    }
    return generateSampleProfile();
  }
} catch (err) {
  console.error('❌ Error fetching profile:', err);
  // Try sessionStorage as fallback
  const sessionProfile = sessionStorage.getItem('userQuizResponses');
  if (sessionProfile) {
    return JSON.parse(sessionProfile);
  }
  return generateSampleProfile();
}
}


/**
* Fetch personality quiz data from sessionStorage
*/
function fetchPersonalityQuizData() {
const data = sessionStorage.getItem('personalityQuizResponses');
if (data) {
  return JSON.parse(data);
}
return {};
}


/**
* Generate sample profile for demonstration
*/
function generateSampleProfile() {
return {
  "What is your favorite color?": "Blue",
  "What do you want your username to be?": "tech_explorer",
  "What's your favorite animal?": "Cats",
  "What is your favorite genre of music?": "Rock",
  "What is your favorite band/musical artist?": "The Beatles",
  "What is your favorite subject?": "Math"
};
}


/* ========== GENERATE COMPREHENSIVE AI ANALYSIS (PROCEDURE) ========== */


/**
* Generate comprehensive AI analysis using both profile + personality data
* Different inputs produce different outputs based on user preferences
*/
async function generateComprehensiveAnalysis(profileData, personalityData, focus, depth) {
console.log('🤖 Generating comprehensive AI analysis...');
console.log('Focus:', focus, 'Depth:', depth);


// Extract key insights from profile data using ITERATION
const profileInsights = [];
const attributeCategories = [
  { key: "What is your favorite color?", label: "Color Preference" },
  { key: "What's your favorite animal?", label: "Animal Preference" },
  { key: "What is your favorite genre of music?", label: "Music Taste" },
  { key: "What is your favorite subject?", label: "Academic Interest" }
];


// ITERATION: Process each profile attribute
attributeCategories.forEach(category => {
  if (profileData[category.key]) {
    profileInsights.push({
      category: category.label,
      value: profileData[category.key]
    });
  }
});


// SELECTION: Count personality trait indicators
let introversionScore = 0;
let extroversionScore = 0;
let thinkingScore = 0;
let feelingScore = 0;
let planningScore = 0;
let spontaneousScore = 0;


// ITERATION through personality responses
Object.values(personalityData).forEach(answer => {
  const answerStr = String(answer).toLowerCase();


  // SELECTION: Categorize responses based on keywords
  if (answerStr.includes('alone') || answerStr.includes('observ') || answerStr.includes('quiet') || answerStr.includes('i_high')) {
    introversionScore++;
  }
  if (answerStr.includes('people') || answerStr.includes('social') || answerStr.includes('out') || answerStr.includes('e_high')) {
    extroversionScore++;
  }
  if (answerStr.includes('logic') || answerStr.includes('fact') || answerStr.includes('analysis') || answerStr.includes('t_high')) {
    thinkingScore++;
  }
  if (answerStr.includes('feeling') || answerStr.includes('empath') || answerStr.includes('emotion') || answerStr.includes('f_high')) {
    feelingScore++;
  }
  if (answerStr.includes('plan') || answerStr.includes('structure') || answerStr.includes('j_high')) {
    planningScore++;
  }
  if (answerStr.includes('spontaneous') || answerStr.includes('flexible') || answerStr.includes('p_high')) {
    spontaneousScore++;
  }
});


// Generate comprehensive analysis combining both datasets
return {
  focus: focus,
  depth: depth,
  profileInsights: profileInsights,
  personalityTraits: {
    social: extroversionScore > introversionScore ? 'Extroverted' : 'Introverted',
    decision: thinkingScore > feelingScore ? 'Analytical' : 'Empathetic',
    lifestyle: planningScore > spontaneousScore ? 'Structured' : 'Spontaneous',
    socialScore: extroversionScore,
    introversionScore: introversionScore,
    thinkingScore: thinkingScore,
    feelingScore: feelingScore
  },
  combinedInsights: generateCombinedInsights(profileData, personalityData, focus, depth)
};
}


/**
* Generate combined insights based on focus area and depth
* Shows how DIFFERENT INPUTS produce DIFFERENT OUTPUTS
*/
function generateCombinedInsights(profile, personality, focus, depth) {
const insights = [];


// Compatibility-focused insights
if (focus === 'compatibility' || focus === 'comprehensive') {
  const music = profile["What is your favorite genre of music?"];
  if (music) {
    if (music.toLowerCase() === 'rock') {
      insights.push("🎸 <strong>Music Compatibility:</strong> Your love for Rock music suggests you appreciate authenticity and emotional depth. You'd connect well with partners who value genuine expression and aren't afraid to show their emotions.");
    } else if (music.toLowerCase() === 'pop') {
      insights.push("🎵 <strong>Music Compatibility:</strong> Your Pop music preference indicates you enjoy mainstream culture and social connection. You'd match well with outgoing partners who enjoy popular activities and staying current with trends.");
    } else if (music.toLowerCase() === 'rap') {
      insights.push("🎤 <strong>Music Compatibility:</strong> Your Rap preference shows you value lyrical complexity and cultural commentary. You'd connect with intellectually curious partners who appreciate depth and social awareness.");
    }
  }
}


// Strengths-focused insights
if (focus === 'strengths' || focus === 'comprehensive') {
  const subject = profile["What is your favorite subject?"];
  if (subject) {
    if (subject.toLowerCase() === 'math' || subject.toLowerCase() === 'science') {
      insights.push("🧮 <strong>Cognitive Strength:</strong> Your interest in " + subject + " reveals strong analytical and problem-solving abilities. You excel at breaking down complex challenges and finding logical solutions.");
    } else if (subject.toLowerCase() === 'english' || subject.toLowerCase() === 'history') {
      insights.push("📚 <strong>Interpersonal Strength:</strong> Your " + subject + " preference indicates excellent communication skills and empathy. You understand context, nuance, and human motivations deeply.");
    }
  }
}


// Communication-focused insights
if (focus === 'communication' || focus === 'comprehensive') {
  const animal = profile["What's your favorite animal?"];
  if (animal) {
    if (animal.toLowerCase() === 'dogs') {
      insights.push("🐕 <strong>Communication Style:</strong> Like dogs, you value loyalty and direct, honest communication. You appreciate when others are straightforward with you and reciprocate with transparency.");
    } else if (animal.toLowerCase() === 'cats') {
      insights.push("🐱 <strong>Communication Style:</strong> Like cats, you value independence and selective engagement. You communicate when it matters and appreciate partners who respect your need for space.");
    } else if (animal.toLowerCase() === 'birds') {
      insights.push("🦜 <strong>Communication Style:</strong> Like birds, you're expressive and social. You communicate frequently and enjoy partners who engage in lively conversations.");
    }
  }
}


// Add depth-specific insights
if (depth === 'deep' || depth === 'moderate') {
  const color = profile["What is your favorite color?"];
  if (color) {
    const colorInsights = {
      'red': '❤️ Your preference for Red suggests passionate energy and boldness in relationships.',
      'blue': '💙 Your preference for Blue indicates a calm, trustworthy nature that provides stability.',
      'green': '💚 Your preference for Green shows growth-oriented thinking and balance.',
      'purple': '💜 Your preference for Purple reveals creativity and depth in emotional connections.'
    };
    const insight = colorInsights[color.toLowerCase()];
    if (insight) {
      insights.push("<strong>Personality Color:</strong> " + insight);
    }
  }
}


// Add comprehensive note if selected
if (focus === 'comprehensive' && depth === 'deep') {
  insights.push("✨ <strong>Holistic Analysis:</strong> Your unique combination of traits creates a multifaceted personality. You blend analytical thinking with emotional awareness, structured planning with spontaneous flexibility. This balance makes you adaptable and able to connect with diverse personality types.");
}


return insights;
}


/* ========== SAVE ANALYSIS TO BACKEND ========== */


/**
* Save the AI analysis and personality data to backend for matchmaking
*/
async function saveAnalysisToBackend(analysis, personalityData) {
try {
  console.log('💾 Saving analysis to backend for matchmaking...');


  const payload = {
    profile_data: {
      personality_quiz: personalityData,
      analysis: {
        focus: analysis.focus,
        depth: analysis.depth,
        personalityTraits: analysis.personalityTraits,
        profileInsights: analysis.profileInsights
      }
    }
  };


  console.log('Payload:', payload);


  const response = await fetch(`${pythonURI}/api/match/save`, {
    method: 'POST',
    credentials: 'include',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify(payload)
  });


  console.log('Save response status:', response.status);


  if (!response.ok) {
    console.error('Failed to save analysis:', response.status);
    return false;
  }


  const data = await response.json();
  console.log('✅ Analysis saved successfully:', data);
  return true;
} catch (err) {
  console.error('❌ Error saving analysis:', err);
  return false;
}
}


/* ========== DISPLAY COMPREHENSIVE ANALYSIS (OUTPUT) ========== */


/**
* Display comprehensive AI analysis (compact terminal style)
*/
function displayComprehensiveAnalysis(analysis, profileData, personalityData) {
const displayDiv = document.getElementById('profile-display');


let html = `<p style="text-align: center; color: #6e7681; margin-bottom: 12px; font-size: 12px;">
  Focus: ${getFocusLabel(analysis.focus)} | Detail: ${getDepthLabel(analysis.depth)}
</p>`;


// Profile Insights Section (compact)
html += '<div style="background: rgba(22, 27, 34, 0.6); padding: 12px; border-radius: 4px; margin-bottom: 10px; border-left: 2px solid #30363d;">';
html += '<div style="color: #7d8590; font-size: 11px; text-transform: uppercase; letter-spacing: 1px; margin-bottom: 8px;">PROFILE DATA</div>';
html += '<div style="display: flex; flex-wrap: wrap; gap: 8px;">';


analysis.profileInsights.forEach(insight => {
  html += `<span style="background: rgba(48, 54, 61, 0.5); padding: 4px 8px; border-radius: 3px; font-size: 12px; color: #8b949e;">${insight.category}: <strong>${insight.value}</strong></span>`;
});


html += '</div></div>';


// Personality Traits Section (compact inline)
html += '<div style="background: rgba(22, 27, 34, 0.6); padding: 12px; border-radius: 4px; margin-bottom: 10px; border-left: 2px solid #30363d;">';
html += '<div style="color: #7d8590; font-size: 11px; text-transform: uppercase; letter-spacing: 1px; margin-bottom: 8px;">PERSONALITY TRAITS</div>';
html += `<div style="display: flex; gap: 12px; flex-wrap: wrap; justify-content: center;">
    <span style="background: rgba(48, 54, 61, 0.5); padding: 6px 10px; border-radius: 3px; font-size: 12px; color: #8b949e;">${analysis.personalityTraits.social === 'Extroverted' ? '👥' : '🧘'} ${analysis.personalityTraits.social}</span>
    <span style="background: rgba(48, 54, 61, 0.5); padding: 6px 10px; border-radius: 3px; font-size: 12px; color: #8b949e;">${analysis.personalityTraits.decision === 'Analytical' ? '🧮' : '❤️'} ${analysis.personalityTraits.decision}</span>
    <span style="background: rgba(48, 54, 61, 0.5); padding: 6px 10px; border-radius: 3px; font-size: 12px; color: #8b949e;">${analysis.personalityTraits.lifestyle === 'Structured' ? '📅' : '🌊'} ${analysis.personalityTraits.lifestyle}</span>
  </div>`;
html += '</div>';


// Combined Insights Section (compact)
if (analysis.combinedInsights.length > 0) {
  html += '<div style="background: rgba(22, 27, 34, 0.6); padding: 12px; border-radius: 4px; border-left: 2px solid #30363d;">';
  html += '<div style="color: #7d8590; font-size: 11px; text-transform: uppercase; letter-spacing: 1px; margin-bottom: 8px;">AI INSIGHTS</div>';


  analysis.combinedInsights.forEach(insight => {
    html += `<div style="padding: 8px; margin: 6px 0; background: rgba(48, 54, 61, 0.3); border-left: 2px solid #485662; border-radius: 2px; font-size: 12px; color: #8b949e; line-height: 1.5;">${insight}</div>`;
  });


  html += '</div>';
}


displayDiv.innerHTML = html;
}


/**
* Helper functions to get readable labels
*/
function getFocusLabel(focus) {
const labels = {
  'compatibility': 'Relationship Compatibility',
  'strengths': 'Personal Strengths & Growth',
  'communication': 'Communication Style',
  'comprehensive': 'Comprehensive Analysis'
};
return labels[focus] || focus;
}


function getDepthLabel(depth) {
const labels = {
  'brief': 'Brief Overview',
  'moderate': 'Moderate Detail',
  'deep': 'Deep Dive'
};
return labels[depth] || depth;
}


/* ========== REMOVE JEKYLL METADATA TEXT ========== */
function removeJekyllMetadata() {
// Find and remove any text nodes or elements containing metadata keywords
const keywords = ['Categories:', 'Breadcrumb:', 'Author:', 'Tags:', 'Reading time:', 'min read'];




function removeTextNodes(element) {
  const walker = document.createTreeWalker(
    element,
    NodeFilter.SHOW_TEXT | NodeFilter.SHOW_ELEMENT,
    null
  );




  const nodesToRemove = [];
  let node;




  while (node = walker.nextNode()) {
    if (node.nodeType === Node.TEXT_NODE) {
      const text = node.textContent.trim();
      if (keywords.some(keyword => text.includes(keyword))) {
        nodesToRemove.push(node.parentElement || node);
      }
    } else if (node.nodeType === Node.ELEMENT_NODE) {
      const text = node.textContent.trim();
      // Only remove if it's a small element (likely metadata) and contains keywords
      if (text.length < 200 && keywords.some(keyword => text.includes(keyword))) {
        // Don't remove if it's our custom content
        if (!node.closest('.container') && !node.closest('header') && !node.id) {
          nodesToRemove.push(node);
        }
      }
    }
  }




  nodesToRemove.forEach(node => {
    if (node && node.parentNode) {
      node.parentNode.removeChild(node);
    }
  });
}




// Remove from body but not our custom elements
const body = document.body;
const customContent = document.querySelector('.container');
const customHeader = document.querySelector('header');




// Process all elements before our custom content
if (customContent) {
  let sibling = body.firstChild;
  while (sibling && sibling !== customContent && sibling !== customHeader) {
    const next = sibling.nextSibling;
    removeTextNodes(sibling);
    sibling = next;
  }
}
}




/* ========== EXPOSE FUNCTIONS FOR ONCLICK HANDLERS ========== */
window.generateAIAnalysis = generateAIAnalysis;
window.showInputSection = showInputSection;




/* ========== INITIALIZE PAGE ON LOAD ========== */
window.addEventListener('DOMContentLoaded', () => {
console.log('🚀 AI Analysis page loaded');


// Remove Jekyll metadata first
removeJekyllMetadata();


// Check if both quizzes are completed
if (!checkQuizzesCompleted()) {
  return; // Will redirect to Krishna's quiz page
}


// Enable dropdown listeners
const focusSelect = document.getElementById('analysis-focus');
const depthSelect = document.getElementById('analysis-depth');


if (focusSelect) {
  focusSelect.addEventListener('change', updateAnalysisButton);
}
if (depthSelect) {
  depthSelect.addEventListener('change', updateAnalysisButton);
}


console.log('✅ AI Analysis page ready');


// Also run metadata removal after a short delay in case Jekyll loads it dynamically
setTimeout(removeJekyllMetadata, 100);
setTimeout(removeJekyllMetadata, 500);
});
</script>




</body>
</html>





