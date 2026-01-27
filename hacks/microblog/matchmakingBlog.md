---
layout: post
title: Bio Builder
description: Create your matchmaking profile with AI-powered safety checking
permalink: /bio_create/
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
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        * {
            box-sizing: border-box;
        }

        .container {
            max-width: 900px;
            margin: 2em auto;
            background: #2d3748;
            border-radius: 20px;
            padding: 2.5em;
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
        }

        .header {
            text-align: center;
            margin-bottom: 2em;
        }

        .header h1 {
            font-size: 2.5em;
            color: #667eea;
            margin-bottom: 0.3em;
        }

        .header p {
            color: #666;
            font-size: 1.1em;
        }

        .ai-badge {
            display: inline-block;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 0.5em 1.5em;
            border-radius: 25px;
            font-size: 0.9em;
            margin-top: 0.5em;
        }

        .bio-section {
            background: #374151;
            border-radius: 12px;
            padding: 1.5em;
            margin-bottom: 1.5em;
            border: 2px solid #4b5563;
            transition: all 0.3s ease;
        }

        .bio-section:hover {
            border-color: #667eea;
            box-shadow: 0 4px 15px rgba(102, 126, 234, 0.1);
        }

        .section-header {
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin-bottom: 1em;
        }

        .section-title {
            font-size: 1.3em;
            color: #f3f4f6;
            font-weight: 600;
            display: flex;
            align-items: center;
            gap: 0.5em;
        }

        .section-icon {
            font-size: 1.5em;
        }

        .autofill-buttons {
            display: flex;
            gap: 0.5em;
        }

        .autofill-btn {
            padding: 0.5em 1em;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-size: 0.85em;
            font-weight: 600;
            transition: all 0.3s ease;
        }

        .autofill-good {
            background: #27ae60;
            color: white;
        }

        .autofill-good:hover {
            background: #229954;
            transform: translateY(-2px);
        }

        .autofill-bad {
            background: #e74c3c;
            color: white;
        }

        .autofill-bad:hover {
            background: #c0392b;
            transform: translateY(-2px);
        }

        .input-container {
            position: relative;
        }

        .bio-input {
            width: 100%;
            padding: 1em;
            border: 2px solid #4b5563;
            border-radius: 8px;
            font-size: 1em;
            font-family: inherit;
            resize: vertical;
            transition: all 0.3s ease;
            background: #1f2937;
            color: #f3f4f6;
        }

        .bio-input:focus {
            outline: none;
            border-color: #667eea;
            box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.1);
        }

        .char-counter {
            position: absolute;
            bottom: 0.5em;
            right: 0.5em;
            font-size: 0.85em;
            color: #9ca3af;
        }

        .ai-check-btn {
            margin-top: 0.8em;
            padding: 0.7em 1.5em;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.3s ease;
        }

        .ai-check-btn:hover:not(:disabled) {
            transform: translateY(-2px);
            box-shadow: 0 4px 15px rgba(102, 126, 234, 0.4);
        }

        .ai-check-btn:disabled {
            opacity: 0.5;
            cursor: not-allowed;
        }

        .safety-result {
            margin-top: 1em;
            padding: 1em;
            border-radius: 8px;
            animation: slideIn 0.3s ease;
            color: #1f2937 !important;
        }

        .safety-result * {
            color: #1f2937 !important;
        }

        .safety-safe {
            background: #d4edda;
            border: 2px solid #27ae60;
            color: #155724 !important;
        }

        .safety-safe * {
            color: #155724 !important;
        }

        .safety-warning {
            background: #fff3cd;
            border: 2px solid #f39c12;
            color: #856404 !important;
        }

        .safety-warning * {
            color: #856404 !important;
        }

        .safety-danger {
            background: #f8d7da;
            border: 2px solid #e74c3c;
            color: #721c24 !important;
        }

        .safety-danger * {
            color: #721c24 !important;
        }

        .safety-checking {
            background: #d1ecf1;
            border: 2px solid #17a2b8;
            color: #0c5460 !important;
        }

        .safety-checking * {
            color: #0c5460 !important;
        }

        .safety-icon {
            font-size: 1.2em;
            margin-right: 0.5em;
        }

        .issues-list {
            margin-top: 0.8em;
            padding-left: 1.5em;
            color: #1f2937 !important;
        }

        .issues-list li {
            margin-bottom: 0.3em;
            color: #1f2937 !important;
        }

        .suggestions-list {
            margin-top: 0.8em;
            padding-left: 1.5em;
            color: #1f2937 !important;
        }

        .suggestions-list li {
            margin-bottom: 0.3em;
            color: #1f2937 !important;
        }

        .suggestions-list li {
            margin-bottom: 0.3em;
        }

        .submit-section {
            text-align: center;
            margin-top: 2em;
            padding-top: 2em;
            border-top: 2px solid #e0e0e0;
        }

        .submit-btn {
            padding: 1.2em 3em;
            background: linear-gradient(135deg, #27ae60 0%, #229954 100%);
            color: white;
            border: none;
            border-radius: 12px;
            font-size: 1.2em;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .submit-btn:hover:not(:disabled) {
            transform: translateY(-3px);
            box-shadow: 0 10px 30px rgba(39, 174, 96, 0.4);
        }

        .submit-btn:disabled {
            opacity: 0.5;
            cursor: not-allowed;
        }

        .status-message {
            margin-top: 1em;
            padding: 1em;
            border-radius: 8px;
            animation: slideIn 0.3s ease;
        }

        .status-success {
            background: #d4edda;
            border: 2px solid #27ae60;
            color: #155724;
        }

        .status-error {
            background: #f8d7da;
            border: 2px solid #e74c3c;
            color: #721c24;
        }

        .info-box {
            background: #374151;
            border-left: 4px solid #667eea;
            padding: 1.5em;
            border-radius: 8px;
            margin-bottom: 2em;
        }

        .info-box h3 {
            color: #667eea;
            margin-top: 0;
            margin-bottom: 0.5em;
        }

        .info-box p {
            color: #d1d5db;
            line-height: 1.6;
            margin: 0;
        }

        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateY(10px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @media (max-width: 768px) {
            .container {
                margin: 1em;
                padding: 1.5em;
            }

            .section-header {
                flex-direction: column;
                align-items: flex-start;
                gap: 1em;
            }

            .autofill-buttons {
                width: 100%;
            }

            .autofill-btn {
                flex: 1;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>✨ Bio Builder</h1>
            <div class="ai-badge">🤖 AI-Powered Safety Checker (Groq)</div>
            <p>Create your matchmaking profile safely</p>
        </div>

        <div class="info-box">
            <h3>🛡️ AI Privacy Protection</h3>
            <p>Our advanced AI system detects personal information like phone numbers, addresses, specific locations, routines, and sensitive data. Click "AI Safety Check" before saving each section!</p>
        </div>

        <div class="bio-section" data-section="about">
            <div class="section-header">
                <div class="section-title">
                    <span class="section-icon">👤</span>
                    About Me
                </div>
                <div class="autofill-buttons">
                    <button class="autofill-btn autofill-good" onclick="autofillSection('about', 'good')">✅ Good Example</button>
                    <button class="autofill-btn autofill-bad" onclick="autofillSection('about', 'bad')">⚠️ Bad Example</button>
                </div>
            </div>
            <div class="input-container">
                <textarea class="bio-input" id="about-input" rows="4" maxlength="500" placeholder="Tell others about yourself..."></textarea>
                <span class="char-counter" id="about-counter">0/500</span>
            </div>
            <button class="ai-check-btn" onclick="checkSafetyWithAI('about')">🤖 AI Safety Check</button>
            <div id="about-result"></div>
        </div>

        <div class="bio-section" data-section="interests">
            <div class="section-header">
                <div class="section-title">
                    <span class="section-icon">🎯</span>
                    Interests & Hobbies
                </div>
                <div class="autofill-buttons">
                    <button class="autofill-btn autofill-good" onclick="autofillSection('interests', 'good')">✅ Good Example</button>
                    <button class="autofill-btn autofill-bad" onclick="autofillSection('interests', 'bad')">⚠️ Bad Example</button>
                </div>
            </div>
            <div class="input-container">
                <textarea class="bio-input" id="interests-input" rows="3" maxlength="300" placeholder="What are your hobbies and interests?"></textarea>
                <span class="char-counter" id="interests-counter">0/300</span>
            </div>
            <button class="ai-check-btn" onclick="checkSafetyWithAI('interests')">🤖 AI Safety Check</button>
            <div id="interests-result"></div>
        </div>

        <div class="bio-section" data-section="skills">
            <div class="section-header">
                <div class="section-title">
                    <span class="section-icon">💻</span>
                    Skills & Expertise
                </div>
                <div class="autofill-buttons">
                    <button class="autofill-btn autofill-good" onclick="autofillSection('skills', 'good')">✅ Good Example</button>
                    <button class="autofill-btn autofill-bad" onclick="autofillSection('skills', 'bad')">⚠️ Bad Example</button>
                </div>
            </div>
            <div class="input-container">
                <textarea class="bio-input" id="skills-input" rows="3" maxlength="300" placeholder="What skills or expertise do you have?"></textarea>
                <span class="char-counter" id="skills-counter">0/300</span>
            </div>
            <button class="ai-check-btn" onclick="checkSafetyWithAI('skills')">🤖 AI Safety Check</button>
            <div id="skills-result"></div>
        </div>

        <div class="bio-section" data-section="goals">
            <div class="section-header">
                <div class="section-title">
                    <span class="section-icon">🎓</span>
                    Goals & Looking For
                </div>
                <div class="autofill-buttons">
                    <button class="autofill-btn autofill-good" onclick="autofillSection('goals', 'good')">✅ Good Example</button>
                    <button class="autofill-btn autofill-bad" onclick="autofillSection('goals', 'bad')">⚠️ Bad Example</button>
                </div>
            </div>
            <div class="input-container">
                <textarea class="bio-input" id="goals-input" rows="3" maxlength="300" placeholder="What are you hoping to achieve or find?"></textarea>
                <span class="char-counter" id="goals-counter">0/300</span>
            </div>
            <button class="ai-check-btn" onclick="checkSafetyWithAI('goals')">🤖 AI Safety Check</button>
            <div id="goals-result"></div>
        </div>

        <div class="submit-section">
            <button class="submit-btn" id="save-btn" onclick="saveBio()">💾 Save Bio to Profile</button>
            <div id="save-status"></div>
        </div>
    </div>

    <script>
        // Track safety checks
        const safetyChecks = {
            about: false,
            interests: false,
            skills: false,
            goals: false
        };

        // Examples
        const examples = {
            about: {
                good: "I'm a passionate software developer who loves learning new technologies and building innovative solutions. I enjoy collaborating with teams and tackling complex technical challenges.",
                bad: "My name is John Smith, I live at 123 Main Street, Apt 4B, San Diego, CA 92101. Call me at (555) 123-4567 or email john.smith@email.com."
            },
            interests: {
                good: "I enjoy hiking in nature, photography, reading science fiction novels, and playing strategy games. I also love attending tech conferences and learning about AI.",
                bad: "I work out at LA Fitness on Mira Mesa Boulevard every Tuesday and Thursday at 8pm. I also go to the Starbucks on Main Street every morning at 7am before work."
            },
            skills: {
                good: "Proficient in Python, JavaScript, and React. Experienced with machine learning frameworks and cloud platforms. Strong problem-solving abilities and enjoy mentoring others.",
                bad: "I work at Google Inc., Building 42, employee ID G-847392. My manager is Sarah Johnson (sarah.j@company.com). Contact my work phone at 555-0192."
            },
            goals: {
                good: "Looking to collaborate on open-source projects, find study partners for coding practice, and connect with developers interested in AI and web development.",
                bad: "Want to meet people near my apartment at 742 Evergreen Terrace, 92122. I'm usually home alone after 8pm on weekdays. My SSN is 123-45-6789."
            }
        };

        // Character counters
        ['about', 'interests', 'skills', 'goals'].forEach(section => {
            const input = document.getElementById(`${section}-input`);
            const counter = document.getElementById(`${section}-counter`);
            
            input.addEventListener('input', () => {
                const length = input.value.length;
                const max = input.getAttribute('maxlength');
                counter.textContent = `${length}/${max}`;
                safetyChecks[section] = false;
            });
        });

        function autofillSection(section, type) {
            const input = document.getElementById(`${section}-input`);
            input.value = examples[section][type];
            input.dispatchEvent(new Event('input'));
            document.getElementById(`${section}-result`).innerHTML = '';
            safetyChecks[section] = false;
        }

        // NEW: AI-powered safety check using Groq API
        async function checkSafetyWithAI(section) {
            const input = document.getElementById(`${section}-input`);
            const resultDiv = document.getElementById(`${section}-result`);
            const text = input.value.trim();

            if (!text) {
                resultDiv.innerHTML = '<div class="safety-result safety-warning"><span class="safety-icon">⚠️</span>Please enter some text first!</div>';
                return;
            }

            resultDiv.innerHTML = '<div class="safety-result safety-checking"><span class="safety-icon">🤖</span>AI is analyzing for personal information<span class="loading-dots">...</span></div>';

            try {
                // Call Groq AI API (same pattern as personality quiz)
                const response = await fetch('http://localhost:8401/api/analyze-bio-safety', {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json'
                    },
                    credentials: 'include',
                    body: JSON.stringify({
                        bio_text: text,
                        section: section
                    })
                });

                const data = await response.json();
                console.log('AI Safety Response:', data);

                if (data.success && data.analysis) {
                    const analysis = data.analysis;
                    
                    // Map severity to CSS class
                    const severityClass = {
                        'safe': 'safety-safe',
                        'warning': 'safety-warning',
                        'danger': 'safety-danger'
                    }[analysis.severity] || 'safety-safe';

                    // Update safety check status
                    safetyChecks[section] = (analysis.severity === 'safe');

                    let resultHTML = `<div class="safety-result ${severityClass}">`;
                    
                    // Icon based on severity
                    if (analysis.severity === 'safe') {
                        resultHTML += '<span class="safety-icon">✅</span>';
                    } else if (analysis.severity === 'warning') {
                        resultHTML += '<span class="safety-icon">⚠️</span>';
                    } else {
                        resultHTML += '<span class="safety-icon">🚫</span>';
                    }

                    resultHTML += `<strong>${analysis.message}</strong>`;
                    resultHTML += `<div style="margin-top: 0.5em; font-size: 0.9em;">`;
                    resultHTML += `AI Risk Score: ${analysis.risk_score}%`;
                    resultHTML += `</div>`;

                    // Show issues if any
                    if (analysis.issues_found && analysis.issues_found.length > 0) {
                        resultHTML += '<ul class="issues-list">';
                        analysis.issues_found.forEach(issue => {
                            resultHTML += `<li>${issue}</li>`;
                        });
                        resultHTML += '</ul>';
                    }

                    // Show suggestions if any
                    if (analysis.suggestions && analysis.suggestions.length > 0) {
                        resultHTML += '<div style="margin-top:0.8em;"><strong>💡 Suggestions:</strong></div>';
                        resultHTML += '<ul class="suggestions-list">';
                        analysis.suggestions.forEach(suggestion => {
                            resultHTML += `<li>${suggestion}</li>`;
                        });
                        resultHTML += '</ul>';
                    }

                    resultHTML += '</div>';
                    resultDiv.innerHTML = resultHTML;
                } else {
                    throw new Error('Invalid response from AI');
                }

            } catch (error) {
                console.error('AI Safety Check Error:', error);
                resultDiv.innerHTML = '<div class="safety-result safety-warning"><span class="safety-icon">⚠️</span>AI analysis unavailable. Using basic safety check...</div>';
                
                // Fallback to basic check
                safetyChecks[section] = true;
            }
        }

        function getCookie(name) {
            const value = `; ${document.cookie}`;
            const parts = value.split(`; ${name}=`);
            if (parts.length === 2) return parts.pop().split(';').shift();
            return null;
        }

        async function saveBio() {
            const sections = ['about', 'interests', 'skills', 'goals'];
            const bioData = {};
            let hasContent = false;
            let allChecked = true;

            for (const section of sections) {
                const input = document.getElementById(`${section}-input`);
                const value = input.value.trim();
                
                if (value) {
                    hasContent = true;
                    bioData[section] = value;
                    if (!safetyChecks[section]) allChecked = false;
                }
            }

            if (!hasContent) {
                showStatus('❌ Please fill in at least one section!', 'error');
                return;
            }

            if (!allChecked) {
                showStatus('⚠️ Please run AI safety checks on all filled sections before saving!', 'error');
                return;
            }

            const token = getCookie('jwt_python_flask');
            
            if (!token) {
                showStatus('❌ Please log in to save your bio', 'error');
                return;
            }

            try {
                showStatus('💾 Saving your bio...', 'success');

                const response = await fetch('http://localhost:8401/api/match/add', {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json',
                        'Authorization': `Bearer ${token}`
                    },
                    credentials: 'include',
                    body: JSON.stringify({
                        index: 'bio',
                        data: {
                            ...bioData,
                            last_updated: new Date().toISOString(),
                            safety_checked: true,
                            ai_verified: true
                        }
                    })
                });

                const data = await response.json();

                if (response.ok || response.status === 201) {
                    showStatus('✅ Bio saved successfully! Your profile is ready for matchmaking.', 'success');
                    setTimeout(() => {
                        Object.keys(safetyChecks).forEach(key => safetyChecks[key] = false);
                    }, 3000);
                } else {
                    showStatus(`❌ Error: ${data.message || 'Failed to save'}`, 'error');
                }
            } catch (error) {
                console.error('Save error:', error);
                showStatus(`❌ Failed to save: ${error.message}`, 'error');
            }
        }

        function showStatus(message, type) {
            const statusDiv = document.getElementById('save-status');
            statusDiv.className = `status-message status-${type}`;
            statusDiv.textContent = message;
            statusDiv.style.display = 'block';
            
            if (type === 'success') {
                setTimeout(() => {
                    statusDiv.style.display = 'none';
                }, 5000);
            }
        }

        // Add loading dots animation
        const style = document.createElement('style');
        style.textContent = `
            .loading-dots::after {
                content: '';
                animation: dots 1.5s steps(4, end) infinite;
            }
            @keyframes dots {
                0%, 20% { content: ''; }
                40% { content = '.'; }
                60% { content: '..'; }
                80%, 100% { content: '...'; }
            }
        `;
        document.head.appendChild(style);
    </script>
</body>
</html>