---
layout: post
title: "Digital Safety & Online Awareness"
description: "Submodule 4 of AI Usage Mini-Quest"
permalink: /microb/
submodule: 4
categories: [CSP, Submodule, Microblogging]
tags: [online safety, matchmaking, submodule]
author: "Nicolas Diaz"
breadcrumb: true
---
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Digital Safety & Online Awareness</title>

<script>
/* ---------- FLASK BACKEND (FORCED, SAFE) ---------- */
const pythonURI = "http://localhost:8401";
</script> 

<style>
/* ---------- OVERRIDE JEKYLL THEME ---------- */
main, article, .content, .post-content {
  background: transparent !important;
}

div[class*="container"],
div[class*="wrapper"],
div[class*="content"] {
  background: transparent !important;
}

:root {
  --bg-dark: #0a0a0a;
  --bg-darker: #050505;
  --card-bg: #111826;
  --card-hover: #1a2332;
  --accent: #7ad7ff;
  --accent-glow: rgba(122, 215, 255, 0.3);
  --accent-dark: #0f6fa4;
  --border: #1d3247;
  --text: #eaeaea;
  --text-dim: #9ca3af;
  --success: #10b981;
  --error: #ef4444;
  --guardian: #10b981;
  --balanced: #7ad7ff;
  --open: #f59e0b;
}

* {
  box-sizing: border-box;
}

/* ---------- ANIMATED BACKGROUND ---------- */
body {
  margin: 0;
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Arial, sans-serif;
  background: linear-gradient(135deg, var(--bg-darker) 0%, var(--bg-dark) 50%, #0a1628 100%) !important;
  background-attachment: fixed;
  color: var(--text);
  display: flex;
  flex-direction: column;
  align-items: center;
  min-height: 100vh;
  position: relative;
  overflow-x: hidden;
}

body::before {
  content: '';
  position: fixed;
  top: -50%;
  left: -50%;
  width: 200%;
  height: 200%;
  background: 
    radial-gradient(circle at 20% 50%, rgba(122, 215, 255, 0.06) 0%, transparent 50%),
    radial-gradient(circle at 80% 80%, rgba(15, 111, 164, 0.08) 0%, transparent 50%);
  animation: gradientFloat 20s ease-in-out infinite;
  pointer-events: none;
  z-index: 0;
}

@keyframes gradientFloat {
  0%, 100% { transform: translate(0, 0) rotate(0deg); }
  33% { transform: translate(-3%, -3%) rotate(3deg); }
  66% { transform: translate(3%, -2%) rotate(-3deg); }
}

h1, h2, h3 {
  margin: 0;
  text-align: center;
}

/* ---------- HEADER WITH GLOW ---------- */
header {
  position: relative;
  width: 100%;
  padding: 70px 20px;
  background: linear-gradient(135deg, #0a2a43 0%, #001119 100%) !important;
  text-align: center;
  border-bottom: 1px solid var(--border);
  box-shadow: 0 10px 40px rgba(0, 0, 0, 0.5);
  z-index: 1;
}

header::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 70%;
  height: 2px;
  background: linear-gradient(90deg, transparent, var(--accent), transparent);
  box-shadow: 0 0 25px var(--accent-glow);
}

header h1 {
  font-size: 52px;
  font-weight: 900;
  background: linear-gradient(135deg, var(--accent) 0%, #ffffff 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  letter-spacing: -1.5px;
  margin-bottom: 16px;
  animation: fadeInDown 0.8s ease-out;
  text-shadow: 0 0 30px var(--accent-glow);
}

header p {
  font-size: 19px;
  color: var(--text-dim);
  font-weight: 300;
  letter-spacing: 0.3px;
  animation: fadeInUp 0.8s ease-out 0.2s both;
}

@keyframes fadeInDown {
  from {
    opacity: 0;
    transform: translateY(-30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* ---------- CONTAINER ---------- */
.container {
  position: relative;
  width: 100%;
  max-width: 1100px;
  margin: 60px auto;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 36px;
  padding: 0 24px;
  z-index: 1;
  background: transparent !important;
}

.container > * {
  background: transparent !important;
}

/* ---------- ENHANCED INFO CARDS ---------- */
.info-card {
  background: var(--card-bg) !important;
  border: 1px solid var(--border) !important;
  border-radius: 20px !important;
  padding: 38px !important;
  width: 100%;
  max-width: 700px;
  text-align: center;
  cursor: pointer;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  position: relative;
  overflow: hidden;
  animation: cardFadeIn 0.6s ease-out backwards;
  box-shadow: none !important;
}

.info-card:nth-child(1) { animation-delay: 0.1s; }
.info-card:nth-child(2) { animation-delay: 0.2s; }
.info-card:nth-child(3) { animation-delay: 0.3s; }

@keyframes cardFadeIn {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.info-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(135deg, var(--accent-glow) 0%, transparent 60%);
  opacity: 0;
  transition: opacity 0.3s ease;
  pointer-events: none;
}

.info-card:hover {
  transform: translateY(-6px) !important;
  box-shadow: 0 20px 50px rgba(0, 0, 0, 0.6), 0 0 30px var(--accent-glow) !important;
  border-color: var(--accent) !important;
  background: var(--card-hover) !important;
}

.info-card:hover::before {
  opacity: 1;
}

.info-card h3 {
  color: var(--accent);
  margin-bottom: 12px;
  font-size: 24px;
  font-weight: 700;
  letter-spacing: -0.5px;
  position: relative;
  z-index: 1;
}

.info-card p {
  color: var(--text-dim);
  font-size: 16px;
  line-height: 1.6;
  position: relative;
  z-index: 1;
}

/* ---------- MODAL WITH BACKDROP BLUR ---------- */
.visual-mode {
  display: none;
  position: fixed;
  inset: 0;
  background: rgba(0, 0, 0, 0.88);
  backdrop-filter: blur(8px);
  z-index: 9999;
  justify-content: center;
  align-items: center;
  animation: fadeIn 0.3s ease-out;
}

@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

.visual-box {
  background: linear-gradient(135deg, #0e1622 0%, #1a2332 100%);
  border: 1px solid var(--border);
  border-radius: 24px;
  padding: 45px;
  width: 90%;
  max-width: 750px;
  max-height: 85vh;
  overflow-y: auto;
  text-align: center;
  box-shadow: 0 25px 60px rgba(0, 0, 0, 0.7), 0 0 40px var(--accent-glow);
  animation: modalSlideUp 0.4s cubic-bezier(0.4, 0, 0.2, 1);
}

@keyframes modalSlideUp {
  from {
    opacity: 0;
    transform: translateY(30px) scale(0.95);
  }
  to {
    opacity: 1;
    transform: translateY(0) scale(1);
  }
}

.visual-box h2 {
  color: var(--accent);
  margin-bottom: 24px;
  font-size: 32px;
  font-weight: 800;
  letter-spacing: -0.5px;
}

.visual-box p {
  white-space: pre-line;
  line-height: 1.8;
  color: var(--text);
  font-size: 16px;
}

/* ---------- ENHANCED FORM STYLING ---------- */
label {
  margin-top: 24px;
  display: block;
  font-weight: 600;
  color: var(--accent);
  font-size: 15px;
  text-align: left;
  letter-spacing: 0.3px;
}

select, input {
  width: 100%;
  margin-top: 10px;
  padding: 14px 16px;
  background: rgba(17, 24, 38, 0.6);
  border-radius: 12px;
  border: 1px solid var(--border);
  color: var(--text);
  font-size: 15px;
  transition: all 0.3s ease;
  backdrop-filter: blur(10px);
}

select:focus, input:focus {
  outline: none;
  border-color: var(--accent);
  background: rgba(17, 24, 38, 0.9);
  box-shadow: 0 0 0 3px var(--accent-glow);
}

select:hover, input:hover {
  border-color: var(--accent);
}

input::placeholder {
  color: var(--text-dim);
  opacity: 0.6;
}

/* ---------- ENHANCED BUTTON ---------- */
button {
  margin-top: 32px;
  padding: 16px 24px;
  width: 100%;
  border-radius: 12px;
  border: none;
  background: linear-gradient(135deg, var(--accent-dark) 0%, var(--accent) 100%);
  color: white;
  font-size: 17px;
  font-weight: 700;
  cursor: pointer;
  transition: all 0.3s ease;
  box-shadow: 0 8px 20px rgba(122, 215, 255, 0.2);
  letter-spacing: 0.5px;
  text-transform: uppercase;
}

button:hover {
  transform: translateY(-2px);
  box-shadow: 0 12px 30px rgba(122, 215, 255, 0.4);
  background: linear-gradient(135deg, var(--accent) 0%, var(--accent-dark) 100%);
}

button:active {
  transform: translateY(0);
}

/* ---------- RESULT BOX ---------- */
#result-box {
  margin-top: 28px;
  padding-top: 28px;
  border-top: 2px solid var(--border);
  text-align: center;
  animation: slideDown 0.4s ease-out;
}

@keyframes slideDown {
  from {
    opacity: 0;
    transform: translateY(-10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

#result-box h3 {
  color: var(--accent);
  margin-bottom: 14px;
  font-size: 22px;
}

#server-status {
  color: var(--accent);
  margin-top: 12px;
  font-weight: 600;
  font-size: 16px;
  padding: 12px;
  border-radius: 8px;
  background: rgba(122, 215, 255, 0.1);
}

/* ---------- PROFILE RESULT DISPLAY ---------- */
.profile-result {
  margin-top: 20px;
  padding: 24px;
  background: rgba(17, 24, 38, 0.6);
  border-radius: 16px;
  border: 2px solid var(--border);
  animation: resultAppear 0.6s ease-out;
}

@keyframes resultAppear {
  from {
    opacity: 0;
    transform: scale(0.95);
  }
  to {
    opacity: 1;
    transform: scale(1);
  }
}

.profile-badge {
  display: inline-block;
  padding: 12px 24px;
  border-radius: 50px;
  font-size: 20px;
  font-weight: 800;
  margin-bottom: 16px;
  text-transform: uppercase;
  letter-spacing: 1px;
}

.profile-badge.guardian {
  background: linear-gradient(135deg, var(--guardian), #059669);
  color: white;
  box-shadow: 0 8px 20px rgba(16, 185, 129, 0.3);
}

.profile-badge.balanced {
  background: linear-gradient(135deg, var(--balanced), #0ea5e9);
  color: white;
  box-shadow: 0 8px 20px rgba(122, 215, 255, 0.3);
}

.profile-badge.open {
  background: linear-gradient(135deg, var(--open), #f97316);
  color: white;
  box-shadow: 0 8px 20px rgba(245, 158, 11, 0.3);
}

.profile-badge.hacker {
  background: linear-gradient(135deg, #dc2626, #7f1d1d);
  color: white;
  box-shadow: 0 8px 20px rgba(220, 38, 38, 0.5);
  animation: pulse 2s infinite;
}

.profile-badge.ninja {
  background: linear-gradient(135deg, #6366f1, #312e81);
  color: white;
  box-shadow: 0 8px 20px rgba(99, 102, 241, 0.5);
  animation: pulse 2s infinite;
}

@keyframes pulse {
  0%, 100% { transform: scale(1); }
  50% { transform: scale(1.05); }
}

.profile-description {
  text-align: left;
  line-height: 1.8;
  color: var(--text);
  margin-top: 16px;
}

.profile-description h4 {
  color: var(--accent);
  margin-top: 16px;
  margin-bottom: 8px;
  font-size: 18px;
}

.profile-description ul {
  list-style: none;
  padding-left: 0;
}

.profile-description li {
  padding: 8px 0;
  padding-left: 24px;
  position: relative;
}

.profile-description li::before {
  content: '✓';
  position: absolute;
  left: 0;
  color: var(--accent);
  font-weight: bold;
}

/* ---------- ERROR STYLING WITH ANIMATION ---------- */
.error {
  border-color: var(--error) !important;
  background: rgba(239, 68, 68, 0.1) !important;
  animation: shake 0.4s ease-in-out;
}

@keyframes shake {
  0%, 100% { transform: translateX(0); }
  25% { transform: translateX(-8px); }
  75% { transform: translateX(8px); }
}

/* ---------- SCROLLBAR STYLING ---------- */
::-webkit-scrollbar {
  width: 10px;
}

::-webkit-scrollbar-track {
  background: var(--bg-dark);
}

::-webkit-scrollbar-thumb {
  background: var(--border);
  border-radius: 5px;
}

::-webkit-scrollbar-thumb:hover {
  background: var(--accent-dark);
}

/* ---------- RESPONSIVE DESIGN ---------- */
@media (max-width: 768px) {
  header h1 {
    font-size: 36px;
  }
  
  header p {
    font-size: 16px;
  }
  
  .info-card {
    padding: 28px !important;
  }
  
  .visual-box {
    padding: 32px;
  }
}
</style>
</head>

<body>

<header>
  <h1>Digital Safety & Online Awareness</h1>
  <p>Learn how to protect yourself in online and matchmaking environments</p>
</header>

<div class="container">
  <div class="info-card" onclick="openVisual('safety')">
    <h3>🛡️ Understanding Online Safety</h3>
    <p>Protect your identity and privacy online.</p>
  </div>

  <div class="info-card" onclick="openVisual('matchmaking')">
    <h3>🔍 Why Matchmaking Safety Matters</h3>
    <p>Recognize risks in anonymous interactions.</p>
  </div>

  <div class="info-card" onclick="openVisual('tips')">
    <h3>💡 Practical Digital Safety Tips</h3>
    <p>Simple habits that reduce online risk.</p>
  </div>
</div>

<!-- ---------- MODAL ---------- -->
<div id="visual-mode" class="visual-mode" onclick="closeVisual(event)">
  <div class="visual-box">
    <h2 id="visual-title"></h2>
    <p id="visual-text"></p>
    <button onclick="closeVisual(event)">Close</button>
  </div>
</div>

<!-- ---------- ACTIVITY ---------- -->
<div class="container">
  <div class="info-card" style="cursor:default;">
    <h3>📝 Digital Safety Reflection</h3>

    <label>How would you describe your online interaction style?</label>
    <select id="style">
      <option value="Cautious and selective">Cautious</option>
      <option value="Balanced and mindful">Balanced</option>
      <option value="Open but aware">Open</option>
    </select>

    <label>Your personal safety principle</label>
    <input id="phrase" placeholder="Example: I verify before trusting">

    <label>Response to suspicious behavior</label>
    <select id="question4">
      <option value="Block immediately">Block immediately</option>
      <option value="Evaluate carefully">Evaluate first</option>
    </select>

    <label>Rule for sharing information</label>
    <select id="question5">
      <option value="Share minimally">Share minimally</option>
      <option value="Share selectively">Share selectively</option>
    </select>

    <label>Top digital safety habit</label>
    <select id="question6">
      <option value="Strong authentication">Strong authentication</option>
      <option value="Clear boundaries">Clear boundaries</option>
    </select>

    <button onclick="submitPersona()">Submit Reflection</button>

    <div id="result-box" style="display:none;">
      <h3>Your Safety Profile</h3>
      <p id="server-status"></p>
      <div id="profile-display"></div>
    </div>
  </div>
</div>

<script>
/* ---------- POPUP CONTENT ---------- */
const visuals = {
  safety: {
    title: "Understanding Online Safety",
    text: "Online safety protects your identity, privacy, and digital presence.\n\nIt includes avoiding scams, managing privacy, and recognizing risks."
  },
  matchmaking: {
    title: "Why Matchmaking Safety Matters",
    text: "Anonymous platforms can enable impersonation and manipulation.\n\nAlways verify identities and set boundaries."
  },
  tips: {
    title: "Practical Digital Safety Tips",
    text: "• Strong passwords\n• Two-factor authentication\n• Verify users\n• Set boundaries\n• Trust instincts"
  }
};

/* ---------- SAFETY PROFILE DEFINITIONS ---------- */
const safetyProfiles = {
  hacker: {
    name: "Elite Hacker",
    badge: "guardian",
    emoji: "💀",
    description: "You are an Elite Hacker - you've unlocked the secret profile! Your knowledge of digital security goes beyond the basics.",
    strengths: [
      "Deep understanding of security vulnerabilities",
      "Advanced threat detection capabilities",
      "Mastery of digital privacy techniques",
      "Ability to think like an attacker to defend better"
    ],
    recommendations: [
      "Use your powers for good, not evil",
      "Consider a career in cybersecurity",
      "Share your knowledge to help others stay safe",
      "Stay ethical - great power requires great responsibility"
    ]
  },
  ninja: {
    name: "Privacy Ninja",
    badge: "balanced",
    emoji: "🥷",
    description: "You are a Privacy Ninja - a master of staying invisible online. You move through the digital world leaving no trace.",
    strengths: [
      "Expert in anonymization techniques",
      "Minimal digital footprint across platforms",
      "Advanced understanding of tracking prevention",
      "Mastery of privacy-focused tools and practices"
    ],
    recommendations: [
      "Share your stealth techniques with friends",
      "Remember to balance privacy with functionality",
      "Keep learning about emerging privacy threats",
      "Teach others the art of digital invisibility"
    ]
  },
  guardian: {
    name: "Digital Guardian",
    badge: "guardian",
    emoji: "🛡️",
    description: "You are a Digital Guardian - highly cautious and security-focused. You prioritize protection above all else.",
    strengths: [
      "Excellent at identifying potential threats",
      "Strong authentication practices",
      "Minimal digital footprint",
      "Quick to block suspicious activity"
    ],
    recommendations: [
      "Consider balancing security with connectivity",
      "Learn about legitimate networking opportunities",
      "Stay updated on emerging social engineering tactics"
    ]
  },
  balanced: {
    name: "Balanced Navigator",
    badge: "balanced",
    emoji: "⚖️",
    description: "You are a Balanced Navigator - you maintain healthy digital boundaries while staying connected. You evaluate risks thoughtfully.",
    strengths: [
      "Good balance between safety and openness",
      "Thoughtful evaluation of situations",
      "Selective information sharing",
      "Adaptable security practices"
    ],
    recommendations: [
      "Continue refining your threat assessment skills",
      "Share your balanced approach with others",
      "Stay vigilant during high-risk activities"
    ]
  },
  open: {
    name: "Aware Explorer",
    badge: "open",
    emoji: "🌐",
    description: "You are an Aware Explorer - open to online connections while maintaining awareness. You balance accessibility with caution.",
    strengths: [
      "Strong social connections online",
      "Aware of basic safety principles",
      "Willing to engage with new opportunities",
      "Good intuition about people"
    ],
    recommendations: [
      "Strengthen your authentication methods",
      "Review privacy settings regularly",
      "Be more selective with personal information",
      "Develop a quicker response to red flags"
    ]
  }
};

function openVisual(id) {
  document.getElementById("visual-title").textContent = visuals[id].title;
  document.getElementById("visual-text").textContent = visuals[id].text;
  document.getElementById("visual-mode").style.display = "flex";
}

function closeVisual(e) {
  if (e.target.id === "visual-mode" || e.target.tagName === "BUTTON") {
    document.getElementById("visual-mode").style.display = "none";
  }
}

// ========== LISTS TO MANAGE PROGRAM COMPLEXITY ==========
const formFields = ['style', 'phrase', 'question4', 'question5', 'question6'];
const questionKeys = ['interaction_style', 'safety_principle', 'reaction', 'sharing_rule', 'priority_habit'];

// ========== PROCEDURE WITH PARAMETERS, RETURN TYPE, AND ALGORITHM ==========
/**
 * Validates and builds profile data from form fields
 * @param {Array} fieldIds - List of form field element IDs
 * @param {Array} questionNames - List of corresponding question keys
 * @returns {Array|null} - Array of profile data objects, or null if validation fails
 */
function buildAndValidateProfileData(fieldIds, questionNames) {
  const profileData = [];
  let allValid = true;
  
  // ITERATION: Loop through all form fields
  for (let i = 0; i < fieldIds.length; i++) {
    const element = document.getElementById(fieldIds[i]);
    const value = element ? element.value.trim() : '';
    
    // SELECTION: Check if field is valid
    if (value === '') {
      allValid = false;
      if (element) {
        element.classList.add('error');
      }
    } else {
      if (element) {
        element.classList.remove('error');
      }
      
      // SEQUENCING: Add valid data in order
      profileData.push({
        question: questionNames[i],
        response: value
      });
    }
  }
  
  // SELECTION: Return data only if all fields are valid
  if (allValid && profileData.length === fieldIds.length) {
    return profileData;
  } else {
    return null;
  }
}

// ========== NEW PROCEDURE: CALCULATE SAFETY PROFILE ==========
/**
 * Calculates user's safety profile type based on their responses
 * @param {Object} responses - Object containing all user responses
 * @returns {String} - Profile type: 'guardian', 'balanced', 'open', or secret profiles
 */
function calculateSafetyProfile(responses) {
  // SECRET EASTER EGGS: Check for special keywords in safety principle
  const principle = responses.principle.toLowerCase();
  
  // List of secret keywords for special profiles
  const hackerKeywords = ['hacker', 'hack', 'exploit', 'penetration', 'pentesting', 'zero day', 'zeroday', 'pwn', 'root', 'shell'];
  const ninjaKeywords = ['ninja', 'stealth', 'invisible', 'ghost', 'phantom', 'shadow', 'anonymous', 'incognito', 'tor', 'vpn'];
  
  // ITERATION: Check each hacker keyword
  for (let i = 0; i < hackerKeywords.length; i++) {
    if (principle.includes(hackerKeywords[i])) {
      return 'hacker';
    }
  }
  
  // ITERATION: Check each ninja keyword
  for (let i = 0; i < ninjaKeywords.length; i++) {
    if (principle.includes(ninjaKeywords[i])) {
      return 'ninja';
    }
  }
  
  // Normal scoring if no secret keywords found
  let score = 0;
  
  // ITERATION: Score each response
  // More cautious answers = higher score
  
  // SELECTION: Score interaction style
  if (responses.style === "Cautious and selective") {
    score += 3;
  } else if (responses.style === "Balanced and mindful") {
    score += 2;
  } else {
    score += 1;
  }
  
  // SELECTION: Score reaction to suspicious behavior
  if (responses.reaction === "Block immediately") {
    score += 2;
  } else {
    score += 1;
  }
  
  // SELECTION: Score information sharing rule
  if (responses.sharing === "Share minimally") {
    score += 2;
  } else {
    score += 1;
  }
  
  // SELECTION: Score safety habit priority
  if (responses.priority === "Strong authentication") {
    score += 2;
  } else {
    score += 1;
  }
  
  // SELECTION: Determine profile based on total score
  if (score >= 8) {
    return 'guardian';
  } else if (score >= 6) {
    return 'balanced';
  } else {
    return 'open';
  }
}

// ========== NEW PROCEDURE: DISPLAY PROFILE RESULT ==========
/**
 * Displays the calculated safety profile to the user
 * @param {String} profileType - The type of profile ('guardian', 'balanced', 'open')
 */
function displayProfileResult(profileType) {
  const profile = safetyProfiles[profileType];
  const displayDiv = document.getElementById('profile-display');
  
  let strengthsHTML = '';
  // ITERATION: Build strengths list
  for (let i = 0; i < profile.strengths.length; i++) {
    strengthsHTML += `<li>${profile.strengths[i]}</li>`;
  }
  
  let recommendationsHTML = '';
  // ITERATION: Build recommendations list
  for (let i = 0; i < profile.recommendations.length; i++) {
    recommendationsHTML += `<li>${profile.recommendations[i]}</li>`;
  }
  
  // SEQUENCING: Build and display the complete profile
  displayDiv.innerHTML = `
    <div class="profile-result">
      <div class="profile-badge ${profile.badge}">
        ${profile.emoji} ${profile.name}
      </div>
      <div class="profile-description">
        <p><strong>${profile.description}</strong></p>
        
        <h4>Your Strengths:</h4>
        <ul>${strengthsHTML}</ul>
        
        <h4>Recommendations:</h4>
        <ul>${recommendationsHTML}</ul>
      </div>
    </div>
  `;
}

// ========== ORIGINAL FUNCTION (ENHANCED WITH PROFILE CALCULATION) ==========
function submitPersona() {
  // CALL TO STUDENT-DEVELOPED PROCEDURE
  const validatedProfileData = buildAndValidateProfileData(formFields, questionKeys);
  
  // SELECTION: Check if validation passed
  if (validatedProfileData === null) {
    document.getElementById("server-status").textContent = "⚠️ Please fill out all fields";
    document.getElementById("result-box").style.display = "block";
    return;
  }
  
  const responses = {
    style: style.value,
    principle: phrase.value,
    reaction: question4.value,
    sharing: question5.value,
    priority: question6.value
  };
  
  // CALL TO NEW PROCEDURE: Calculate safety profile
  const profileType = calculateSafetyProfile(responses);
  
  document.getElementById("result-box").style.display = "block";
  document.getElementById("server-status").textContent = "⏳ Analyzing your profile...";
  
  // CALL TO NEW PROCEDURE: Display the profile result
  setTimeout(() => {
    displayProfileResult(profileType);
    document.getElementById("server-status").textContent = "✅ Profile generated!";
  }, 800);
  
  /* ---------- MICROBLOG POST ---------- */
  fetch(`${pythonURI}/api/microblog`, {
    method: "POST",
    credentials: "include",
    headers: {
      "Content-Type": "application/json",
      "X-Origin": "client"
    },
    body: JSON.stringify({
      content: "Digital Safety Reflection",
      data: responses,
      topicPath: "/digital-famine/microblog/microb/"
    })
  })
  .catch(err => console.error("Microblog error:", err));
  
  /* ---------- MATCHMAKING SAVE (JWT REQUIRED) ---------- */
  fetch(`${pythonURI}/api/match/save-profile-json`, {
    method: "POST",
    credentials: "include",
    headers: {
      "Content-Type": "application/json"
    },
    body: JSON.stringify({
      profile_data: validatedProfileData
    })
  })
  .then(res => {
    if (!res.ok) {
      throw new Error(`HTTP error! status: ${res.status}`);
    }
    return res.json();
  })
  .then(data => {
    console.log("Save response:", data);
  })
  .catch(err => {
    console.error("Save error:", err);
  });
}
</script>

</body>
</html>