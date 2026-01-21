---
layout: post
title: "Personality Matchmaking Quiz"
description: "Discover your personality type for better connections"
permalink: digital-matchmaking/matchmaking/microb/
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

/* Hide Jekyll metadata boxes but keep title */
.page-meta,
.post-meta,
[class*="breadcrumb"]:not(.progress-container):not(.quiz-card),
[class*="Breadcrumb"]:not(.progress-container):not(.quiz-card),
[class*="category"]:not(.progress-container):not(.quiz-card),
[class*="Category"]:not(.progress-container):not(.quiz-card),
[class*="categories"]:not(.progress-container):not(.quiz-card),
[class*="Categories"]:not(.progress-container):not(.quiz-card),
[class*="tag"]:not(.progress-container):not(.quiz-card),
[class*="Tag"]:not(.progress-container):not(.quiz-card),
[class*="author"]:not(.progress-container):not(.quiz-card),
[class*="Author"]:not(.progress-container):not(.quiz-card),
[class*="reading-time"],
[class*="read-time"],
.meta-info,
.entry-meta,
.breadcrumbs,
.tags,
.categories,
nav[class*="bread"],
.taxonomy,
.post-info,
.article-meta {
  display: none !important;
  visibility: hidden !important;
  height: 0 !important;
  overflow: hidden !important;
}

/* Only hide metadata in Jekyll-specific header containers, not our custom header */
.page-header:not(header) > *:not(h1):not(.page-title):not([class*="title"]),
.post-header:not(header) > *:not(h1):not(.post-title):not([class*="title"]) {
  display: none !important;
}

:root {
  --bg-dark: #1a1a2e;
  --bg-darker: #0f0f1e;
  --card-bg: #16213e;
  --card-hover: #1f2c4a;
  --accent: #ff6b9d;
  --accent-glow: rgba(255, 107, 157, 0.4);
  --accent-dark: #c2185b;
  --accent-light: #ff8fab;
  --border: #2d3561;
  --text: #f0f0f0;
  --text-dim: #a8a8b3;
  --success: #4caf50;
  --error: #ef4444;
  --guardian: #4caf50;
  --balanced: #ff6b9d;
  --open: #ffa726;
}

* {
  box-sizing: border-box;
}

/* ---------- ANIMATED BACKGROUND ---------- */
body {
  margin: 0;
  font-family: 'Poppins', 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Arial, sans-serif;
  background: linear-gradient(135deg, #1a1a2e 0%, #2d1b3d 50%, #1f1635 100%) !important;
  background-attachment: fixed;
  color: var(--text);
  display: flex;
  flex-direction: column;
  align-items: center;
  min-height: 100vh;
  position: relative;
  overflow-x: hidden;
  overflow-y: auto;
}

body::before {
  content: '💕';
  position: fixed;
  top: -50%;
  left: -50%;
  width: 200%;
  height: 200%;
  background:
    radial-gradient(circle at 20% 50%, rgba(255, 107, 157, 0.08) 0%, transparent 50%),
    radial-gradient(circle at 80% 80%, rgba(194, 24, 91, 0.1) 0%, transparent 50%);
  animation: gradientFloat 20s ease-in-out infinite;
  pointer-events: none;
  z-index: 0;
  font-size: 200px;
  opacity: 0.02;
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
  padding: 16px 20px 12px;
  background: linear-gradient(135deg, rgba(255, 107, 157, 0.1) 0%, rgba(194, 24, 91, 0.05) 100%) !important;
  text-align: center;
  border-bottom: 2px solid var(--accent);
  box-shadow: 0 4px 20px rgba(255, 107, 157, 0.2);
  z-index: 1;
  backdrop-filter: blur(10px);
}

header::after {
  content: '💖';
  position: absolute;
  bottom: -12px;
  left: 50%;
  transform: translateX(-50%);
  font-size: 20px;
  filter: drop-shadow(0 0 10px var(--accent-glow));
}

header h1 {
  font-size: 28px;
  font-weight: 800;
  background: linear-gradient(135deg, var(--accent) 0%, var(--accent-light) 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  letter-spacing: -0.5px;
  margin-bottom: 4px;
  animation: fadeInDown 0.8s ease-out;
}

header p {
  font-size: 13px;
  color: var(--text-dim);
  font-weight: 400;
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
  max-width: 600px;
  margin: 12px auto 16px;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 12px;
  padding: 0 16px;
  z-index: 1;
  background: transparent !important;
}

.container > * {
  background: transparent !important;
}

/* ---------- ENHANCED INFO CARDS ---------- */
.info-card {
  background: rgba(255, 255, 255, 0.03) !important;
  border: 1px solid rgba(255, 107, 157, 0.2) !important;
  border-radius: 24px !important;
  padding: 20px !important;
  width: 100%;
  max-width: 600px;
  text-align: center;
  cursor: pointer;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  position: relative;
  overflow: visible;
  animation: cardFadeIn 0.6s ease-out backwards;
  box-shadow:
    0 4px 24px rgba(0, 0, 0, 0.4),
    inset 0 1px 0 rgba(255, 255, 255, 0.05) !important;
  backdrop-filter: blur(20px);
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
  right: 0;
  bottom: 0;
  border-radius: 24px;
  padding: 1px;
  background: linear-gradient(135deg, rgba(255, 107, 157, 0.4), rgba(255, 139, 171, 0.1));
  -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
  -webkit-mask-composite: xor;
  mask-composite: exclude;
  opacity: 0;
  transition: opacity 0.3s ease;
  pointer-events: none;
}

.info-card:hover {
  transform: translateY(-2px) scale(1.01) !important;
  box-shadow:
    0 8px 32px rgba(255, 107, 157, 0.25),
    inset 0 1px 0 rgba(255, 255, 255, 0.1) !important;
  border-color: rgba(255, 107, 157, 0.4) !important;
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
  margin-top: 14px;
  padding: 13px 20px;
  width: 100%;
  border-radius: 30px;
  border: none;
  background: linear-gradient(135deg, #ff6b9d 0%, #ff8fab 100%);
  color: white;
  font-size: 14px;
  font-weight: 700;
  cursor: pointer;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  box-shadow:
    0 4px 16px rgba(255, 107, 157, 0.4),
    inset 0 1px 0 rgba(255, 255, 255, 0.2);
  letter-spacing: 0.5px;
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
  background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
  transition: left 0.5s ease;
}

button:hover::before {
  left: 100%;
}

button:hover {
  transform: translateY(-2px) scale(1.02);
  box-shadow:
    0 8px 24px rgba(255, 107, 157, 0.5),
    inset 0 1px 0 rgba(255, 255, 255, 0.3);
  background: linear-gradient(135deg, #ff8fab 0%, #ffa3bb 100%);
}

button:active {
  transform: translateY(0) scale(0.98);
}

button:disabled {
  opacity: 0.4;
  cursor: not-allowed;
  transform: none;
}

button:disabled:hover {
  transform: none;
  box-shadow: 0 4px 16px rgba(255, 107, 157, 0.4);
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

/* ---------- PROGRESS BAR ---------- */
.progress-container {
  width: 100%;
  max-width: 600px;
  margin-bottom: 8px;
  text-align: center;
}

.progress-bar {
  width: 100%;
  height: 8px;
  background: rgba(255, 255, 255, 0.05);
  border-radius: 20px;
  overflow: hidden;
  border: none;
  position: relative;
  box-shadow: inset 0 2px 4px rgba(0, 0, 0, 0.3);
}

.progress-bar::after {
  content: '';
  position: absolute;
  left: 0;
  top: 0;
  height: 100%;
  width: var(--progress, 0%);
  background: linear-gradient(90deg, #ff6b9d 0%, #ff8fab 50%, #ffa3bb 100%);
  transition: width 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  box-shadow:
    0 0 20px rgba(255, 107, 157, 0.6),
    inset 0 1px 0 rgba(255, 255, 255, 0.3);
  border-radius: 20px;
}

.progress-text {
  margin-top: 4px;
  color: var(--accent-light);
  font-size: 11px;
  font-weight: 600;
  letter-spacing: 0.5px;
}

/* ---------- QUIZ STYLING ---------- */
.quiz-card {
  min-height: 280px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

#quiz-container {
  flex: 1;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.question-slide {
  animation: slideIn 0.4s cubic-bezier(0.4, 0, 0.2, 1);
}

@keyframes slideIn {
  from {
    opacity: 0;
    transform: translateX(30px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

.question-title {
  font-size: 16px;
  color: var(--accent-light);
  margin-bottom: 12px;
  font-weight: 700;
  text-align: center;
  line-height: 1.4;
}

.question-options {
  display: flex;
  flex-direction: column;
  gap: 8px;
  margin-top: 8px;
}

.option-btn {
  padding: 12px 16px;
  background: rgba(255, 255, 255, 0.02);
  border: 1px solid rgba(255, 107, 157, 0.2);
  border-radius: 16px;
  color: var(--text);
  font-size: 13px;
  cursor: pointer;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  text-align: left;
  width: 100%;
  margin: 0;
  font-weight: 500;
  position: relative;
  overflow: hidden;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.2);
}

.option-btn::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(255, 107, 157, 0.1), transparent);
  transition: left 0.5s ease;
}

.option-btn:hover::before {
  left: 100%;
}

.option-btn:hover {
  border-color: rgba(255, 107, 157, 0.5);
  background: rgba(255, 107, 157, 0.08);
  transform: translateX(4px);
  box-shadow: 0 4px 16px rgba(255, 107, 157, 0.2);
}

.option-btn.selected {
  border-color: var(--accent);
  background: linear-gradient(135deg, rgba(255, 107, 157, 0.2) 0%, rgba(255, 139, 171, 0.15) 100%);
  box-shadow:
    0 4px 16px rgba(255, 107, 157, 0.3),
    inset 0 1px 0 rgba(255, 255, 255, 0.1);
  color: var(--accent-light);
}

.option-btn.selected::after {
  content: '✓';
  position: absolute;
  right: 14px;
  top: 50%;
  transform: translateY(-50%);
  color: var(--accent);
  font-weight: bold;
  font-size: 16px;
}

/* ---------- FREE RESPONSE INPUT ---------- */
.free-response-input {
  width: 100%;
  padding: 16px;
  background: rgba(255, 255, 255, 0.02);
  border: 1px solid rgba(255, 107, 157, 0.2);
  border-radius: 16px;
  color: var(--text);
  font-size: 14px;
  font-family: inherit;
  resize: vertical;
  min-height: 120px;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.2);
  line-height: 1.6;
}

.free-response-input::placeholder {
  color: var(--text-dim);
  opacity: 0.5;
}

.free-response-input:focus {
  outline: none;
  border-color: var(--accent);
  background: rgba(255, 107, 157, 0.05);
  box-shadow: 0 4px 16px rgba(255, 107, 157, 0.2);
}

.free-response-input:hover {
  border-color: rgba(255, 107, 157, 0.4);
}

.button-container {
  display: flex;
  gap: 10px;
  margin-top: 14px;
}

.button-container button {
  flex: 1;
  margin: 0;
}

#prev-btn {
  background: transparent;
  border: 2px solid rgba(255, 107, 157, 0.5);
  color: var(--accent-light);
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.2);
}

#prev-btn:hover {
  background: rgba(255, 107, 157, 0.1);
  border-color: var(--accent);
  box-shadow: 0 4px 16px rgba(255, 107, 157, 0.3);
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

  .question-title {
    font-size: 19px;
  }

  .option-btn {
    padding: 16px 20px;
    font-size: 15px;
  }
}
</style>
</head>

<body>

<header>
  <h1>💕 Find Your Perfect Match</h1>
  <p>Discover your unique personality type</p>
</header>

<!-- ---------- PERSONALITY QUIZ ---------- -->
<div class="container">
  <!-- Progress Bar -->
  <div class="progress-container">
    <div class="progress-bar" id="progress-bar"></div>
    <p class="progress-text" id="progress-text">Question 1 of 13</p>
  </div>

  <!-- Quiz Card -->
  <div class="info-card quiz-card" style="cursor:default;">
    <div id="quiz-container">
      <!-- Questions will be injected here dynamically -->
    </div>

    <div class="button-container">
      <button id="prev-btn" onclick="previousQuestion()" style="display:none;">← Previous</button>
      <button id="next-btn" onclick="nextQuestion()">Next →</button>
      <button id="submit-btn" onclick="submitQuiz()" style="display:none;">Get My Personality Type ✨</button>
    </div>
  </div>

  <!-- Result Display -->
  <div id="result-box" class="info-card" style="display:none; cursor:default;">
    <h3>🎯 Your Personality Type</h3>
    <p id="server-status"></p>
    <div id="profile-display"></div>
  </div>
</div>

<script>
/* ========== PERSONALITY QUIZ QUESTIONS ========== */
const quizQuestions = [
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
    question: "Describe your ideal date or hangout. What would you do and why?",
    type: "freeResponse",
    placeholder: "Share your thoughts... (e.g., coffee shop chat, adventure activity, cozy movie night)"
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
    question: "What's something you're passionate about and why does it matter to you?",
    type: "freeResponse",
    placeholder: "Tell us about your passion... (e.g., art, helping others, solving problems)"
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
    question: "If you could change one thing about the world, what would it be and why?",
    type: "freeResponse",
    placeholder: "Share your vision for a better world..."
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

/* ========== QUIZ STATE ========== */
let currentQuestion = 0;
let answers = {};

/* ========== QUIZ NAVIGATION FUNCTIONS ========== */

/**
 * Initialize and render the quiz
 */
function initQuiz() {
  renderQuestion();
  updateProgress();
}

/**
 * Render current question
 */
function renderQuestion() {
  const question = quizQuestions[currentQuestion];
  const container = document.getElementById('quiz-container');

  let contentHTML = '';

  if (question.type === 'freeResponse') {
    // Free-response textarea
    const savedAnswer = answers[question.id] || '';
    contentHTML = `
      <textarea
        id="free-response-${question.id}"
        class="free-response-input"
        placeholder="${question.placeholder}"
        oninput="saveFreeResponse(${question.id}, this.value)"
        rows="5">${savedAnswer}</textarea>
    `;
  } else {
    // Multiple choice options
    question.options.forEach((option, index) => {
      const isSelected = answers[question.id] === option.value;
      contentHTML += `
        <button class="option-btn ${isSelected ? 'selected' : ''}"
                onclick="selectOption(${question.id}, '${option.value}', this)">
          ${option.text}
        </button>
      `;
    });
  }

  container.innerHTML = `
    <div class="question-slide">
      <h3 class="question-title">${question.question}</h3>
      <div class="question-options">
        ${contentHTML}
      </div>
    </div>
  `;

  updateButtons();
}

/**
 * Select an option for current question
 */
function selectOption(questionId, value, element) {
  answers[questionId] = value;

  // Update UI
  document.querySelectorAll('.option-btn').forEach(btn => {
    btn.classList.remove('selected');
  });
  element.classList.add('selected');

  // Enable next/submit button
  updateButtons();
}

/**
 * Save free-response answer
 */
function saveFreeResponse(questionId, value) {
  answers[questionId] = value.trim();
  updateButtons();
}

/**
 * Navigate to next question
 */
function nextQuestion() {
  const currentQ = quizQuestions[currentQuestion];
  const answer = answers[currentQ.id];

  // Validate answer based on question type
  if (!answer || (currentQ.type === 'freeResponse' && answer.length < 3)) {
    if (currentQ.type === 'freeResponse') {
      alert('Please write at least a few words before continuing');
    } else {
      alert('Please select an answer before continuing');
    }
    return;
  }

  if (currentQuestion < quizQuestions.length - 1) {
    currentQuestion++;
    renderQuestion();
    updateProgress();
  }
}

/**
 * Navigate to previous question
 */
function previousQuestion() {
  if (currentQuestion > 0) {
    currentQuestion--;
    renderQuestion();
    updateProgress();
  }
}

/**
 * Update button visibility and states
 */
function updateButtons() {
  const prevBtn = document.getElementById('prev-btn');
  const nextBtn = document.getElementById('next-btn');
  const submitBtn = document.getElementById('submit-btn');

  const currentQ = quizQuestions[currentQuestion];
  let hasAnswer = false;

  if (currentQ.type === 'freeResponse') {
    // For free response, check if there's text (at least 3 characters)
    hasAnswer = answers[currentQ.id] && answers[currentQ.id].length >= 3;
  } else {
    // For multiple choice, just check if answered
    hasAnswer = !!answers[currentQ.id];
  }

  // Show/hide previous button
  prevBtn.style.display = currentQuestion > 0 ? 'block' : 'none';

  // Show next or submit button
  if (currentQuestion === quizQuestions.length - 1) {
    nextBtn.style.display = 'none';
    submitBtn.style.display = 'block';
    submitBtn.disabled = !hasAnswer;
  } else {
    nextBtn.style.display = 'block';
    submitBtn.style.display = 'none';
    nextBtn.disabled = !hasAnswer;
  }
}

/**
 * Update progress bar
 */
function updateProgress() {
  const progress = ((currentQuestion + 1) / quizQuestions.length) * 100;
  const progressBar = document.getElementById('progress-bar');
  const progressText = document.getElementById('progress-text');

  progressBar.style.setProperty('--progress', `${progress}%`);
  progressText.textContent = `Question ${currentQuestion + 1} of ${quizQuestions.length}`;
}

/* ========== AI PERSONALITY ANALYSIS ========== */

/**
 * Call backend API to analyze personality (proxies to Claude API)
 */
async function analyzePersonalityWithAI(responses) {
  console.log('📝 Calling backend AI analysis API...');

  try {
    const response = await fetch(`${pythonURI}/api/analyze-personality`, {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json'
      },
      credentials: 'include',
      body: JSON.stringify({
        responses: responses
      })
    });

    console.log('📡 Backend API Response Status:', response.status);

    if (!response.ok) {
      const errorData = await response.json().catch(() => ({}));
      console.error('❌ API Error Details:', errorData);

      // If backend returns fallback in error response, use it
      if (errorData.fallback) {
        console.log('✨ Using fallback from backend');
        return errorData.fallback;
      }

      throw new Error(`API error: ${response.status} - ${JSON.stringify(errorData)}`);
    }

    const result = await response.json();
    console.log('✅ AI Response received:', result);
    console.log('✨ Personality type:', result.type_name);
    return result;

  } catch (error) {
    console.error('❌ AI Analysis Error:', error);
    console.log('⚠️ Using fallback personality type');

    // Return fallback personality
    return {
      type_name: "The Unique Individual",
      emoji: "✨",
      description: "You have a unique blend of traits that makes you special. Your personality combines elements of different types in interesting ways.",
      strengths: [
        "Adaptable to different situations",
        "Open to new experiences",
        "Thoughtful and reflective",
        "Balanced perspective"
      ],
      recommendations: [
        "Continue exploring what makes you unique",
        "Connect with people who appreciate your complexity",
        "Embrace your multifaceted nature"
      ]
    };
  }
}

/**
 * Display AI-generated personality result
 */
function displayPersonalityResult(personality) {
  const displayDiv = document.getElementById('profile-display');

  let strengthsHTML = '';
  personality.strengths.forEach(strength => {
    strengthsHTML += `<li>${strength}</li>`;
  });

  let recommendationsHTML = '';
  personality.recommendations.forEach(rec => {
    recommendationsHTML += `<li>${rec}</li>`;
  });

  displayDiv.innerHTML = `
    <div class="profile-result">
      <div class="profile-badge balanced">
        ${personality.emoji} ${personality.type_name}
      </div>
      <div class="profile-description">
        <p><strong>${personality.description}</strong></p>

        <h4>Your Strengths:</h4>
        <ul>${strengthsHTML}</ul>

        <h4>Perfect Matches:</h4>
        <ul>${recommendationsHTML}</ul>
      </div>
    </div>
  `;
}

/**
 * Submit quiz and get personality type
 */
async function submitQuiz() {
  // Check all questions answered
  if (Object.keys(answers).length !== quizQuestions.length) {
    alert('Please answer all questions');
    return;
  }

  // Show result box with loading state
  document.getElementById("result-box").style.display = "block";
  document.getElementById("server-status").innerHTML = '⏳ Analyzing your personality<span class="loading-dots"></span>';
  document.getElementById("profile-display").innerHTML = '';

  // Scroll to results
  document.getElementById("result-box").scrollIntoView({ behavior: 'smooth' });

  // Prepare response data
  const responseData = quizQuestions.map(q => {
    if (q.type === 'freeResponse') {
      // Free-response: send the user's text directly
      return {
        question: q.question,
        answer: answers[q.id] || '',
        type: 'freeResponse'
      };
    } else {
      // Multiple choice: send the selected option text
      return {
        question: q.question,
        answer: q.options.find(opt => opt.value === answers[q.id])?.text || '',
        type: 'multipleChoice'
      };
    }
  });

  // Get AI analysis
  const personality = await analyzePersonalityWithAI(responseData);

  // Display result
  setTimeout(() => {
    displayPersonalityResult(personality);
    document.getElementById("server-status").textContent = "✅ Your personality type is ready!";
  }, 500);

  /* ---------- SAVE TO LOCAL STORAGE (NO AUTH REQUIRED) ---------- */
  try {
    localStorage.setItem('personality_data', JSON.stringify({
      personality_type: personality.type_name,
      personality_emoji: personality.emoji,
      personality_description: personality.description,
      timestamp: new Date().toISOString()
    }));
    console.log("✅ Personality saved to local storage");
  } catch (err) {
    console.error("❌ Local storage error:", err);
  }

  /* ---------- SAVE TO BACKEND (profile_setups.json) ---------- */
  // Save personality type to profile_setups.json
  fetch(`${pythonURI}/api/match/add`, {
    method: "POST",
    credentials: "include",
    headers: {
      "Content-Type": "application/json"
    },
    body: JSON.stringify({
      index: "personality_type",
      data: personality.type_name
    })
  })
  .then(res => {
    if (res.ok) {
      console.log("✅ Personality type saved to profile_setups.json");
    } else {
      console.log("ℹ️ Personality type save failed (login required)");
    }
  })
  .catch(err => console.log("ℹ️ Personality type save error:", err.message));

  // Save personality emoji to profile_setups.json
  fetch(`${pythonURI}/api/match/add`, {
    method: "POST",
    credentials: "include",
    headers: {
      "Content-Type": "application/json"
    },
    body: JSON.stringify({
      index: "personality_emoji",
      data: personality.emoji
    })
  })
  .then(res => {
    if (res.ok) {
      console.log("✅ Personality emoji saved to profile_setups.json");
    } else {
      console.log("ℹ️ Personality emoji save failed");
    }
  })
  .catch(err => console.log("ℹ️ Personality emoji save error:", err.message));

  // Save full quiz responses to profile_setups.json
  fetch(`${pythonURI}/api/match/add`, {
    method: "POST",
    credentials: "include",
    headers: {
      "Content-Type": "application/json"
    },
    body: JSON.stringify({
      index: "personality_quiz_responses",
      data: responseData
    })
  })
  .then(res => {
    if (res.ok) {
      console.log("✅ Quiz responses saved to profile_setups.json");
    } else {
      console.log("ℹ️ Quiz responses save failed (login required)");
    }
  })
  .catch(err => console.log("ℹ️ Quiz responses save error:", err.message));

  // Save personality description
  fetch(`${pythonURI}/api/match/add`, {
    method: "POST",
    credentials: "include",
    headers: {
      "Content-Type": "application/json"
    },
    body: JSON.stringify({
      index: "personality_description",
      data: personality.description
    })
  })
  .then(res => {
    if (res.ok) {
      console.log("✅ Personality description saved to profile_setups.json");
    } else {
      console.log("ℹ️ Personality description save failed");
    }
  })
  .catch(err => console.log("ℹ️ Personality description save error:", err.message));

  /* ---------- OPTIONAL: ALSO SAVE TO MICROBLOG ---------- */
  fetch(`${pythonURI}/api/microblog`, {
    method: "POST",
    credentials: "include",
    headers: {
      "Content-Type": "application/json",
      "X-Origin": "client"
    },
    body: JSON.stringify({
      content: `Personality Quiz: ${personality.type_name}`,
      data: { personality_type: personality.type_name },
      topicPath: "/digital-matchmaking/matchmaking/microb/"
    })
  })
  .then(res => {
    if (res.ok) console.log("✅ Microblog post created");
    else console.log("ℹ️ Microblog post failed (login required)");
  })
  .catch(err => console.log("ℹ️ Microblog error:", err.message));
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

/* ========== INITIALIZE QUIZ ON PAGE LOAD ========== */
window.addEventListener('DOMContentLoaded', () => {
  // Remove Jekyll metadata first
  removeJekyllMetadata();
  // Then initialize quiz
  initQuiz();

  // Also run metadata removal after a short delay in case Jekyll loads it dynamically
  setTimeout(removeJekyllMetadata, 100);
  setTimeout(removeJekyllMetadata, 500);
});
</script>

</body>
</html>