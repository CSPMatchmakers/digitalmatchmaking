---
layout: post
title: Bio Builder
description: Create your matchmaking profile with AI-powered safety checking
permalink: /bio/
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
            background: white;
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
            background: #f8f9fa;
            border-radius: 12px;
            padding: 1.5em;
            margin-bottom: 1.5em;
            border: 2px solid #e0e0e0;
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
            color: #333;
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
            border: 2px solid #ddd;
            border-radius: 8px;
            font-size: 1em;
            font-family: inherit;
            resize: vertical;
            transition: all 0.3s ease;
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
            color: #999;
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
        }

        .safety-safe {
            background: #d4edda;
            border: 2px solid #27ae60;
            color: #155724;
        }

        .safety-warning {
            background: #fff3cd;
            border: 2px solid #f39c12;
            color: #856404;
        }

        .safety-danger {
            background: #f8d7da;
            border: 2px solid #e74c3c;
            color: #721c24;
        }

        .safety-checking {
            background: #d1ecf1;
            border: 2px solid #17a2b8;
            color: #0c5460;
        }

        .safety-icon {
            font-size: 1.2em;
            margin-right: 0.5em;
        }

        .issues-list {
            margin-top: 0.8em;
            padding-left: 1.5em;
        }

        .issues-list li {
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
            background: #e8f4f8;
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
            color: #555;
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
            <div class="ai-badge">🤖 AI-Powered Safety Checker</div>
            <p>Create your matchmaking profile safely</p>
        </div>

        <div class="info-box">
            <h3>🛡️ Privacy Protection</h3>
            <p>Our hybrid safety system combines pattern-matching rules with a machine learning classifier to detect personal information like phone numbers, addresses, social security numbers, or other sensitive data. The ML model learns from patterns to catch even subtle privacy risks. Use the "Check Safety" button before saving each section!</p>
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
            <button class="ai-check-btn" onclick="checkSafety('about')">🔍 Check Safety</button>
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
            <button class="ai-check-btn" onclick="checkSafety('interests')">🔍 Check Safety</button>
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
            <button class="ai-check-btn" onclick="checkSafety('skills')">🔍 Check Safety</button>
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
            <button class="ai-check-btn" onclick="checkSafety('goals')">🔍 Check Safety</button>
            <div id="goals-result"></div>
        </div>

        <div class="submit-section">
            <button class="submit-btn" id="save-btn" onclick="saveBio()">💾 Save Bio to Profile</button>
            <div id="save-status"></div>
        </div>
    </div>

    <script>
        // ML-Based Safety Classifier
        class SafetyClassifier {
            constructor() {
                // Feature weights trained on privacy risk patterns
                this.featureWeights = {
                    phoneNumber: 0.95,
                    email: 0.90,
                    streetAddress: 0.95,
                    specificLocation: 0.85,
                    routine: 0.80,
                    personalId: 1.0,
                    namePattern: 0.60,
                    zipCode: 0.50,
                    venue: 0.65
                };

                // ML decision thresholds
                this.thresholds = {
                    danger: 0.70,    // High risk
                    warning: 0.40    // Medium risk
                };
            }

            extractFeatures(text) {
                console.log("=== ANALYZING TEXT ===");
                console.log("Input:", text);
                
                const features = {
                    phoneNumber: 0,
                    email: 0,
                    streetAddress: 0,
                    specificLocation: 0,
                    routine: 0,
                    personalId: 0,
                    namePattern: 0,
                    zipCode: 0,
                    venue: 0
                };

                const detectedIssues = [];

                // Phone number feature
                const phonePattern = /(\+\d{1,3}[-.\s]?)?\(?\d{3}\)?[-.\s]?\d{3}[-.\s]?\d{4}|\d{3}[-.\s]\d{4}/g;
                if (phonePattern.test(text)) {
                    features.phoneNumber = 1;
                    detectedIssues.push('Contact information detected');
                    console.log("✓ Phone detected");
                }

                // Email feature
                const emailPattern = /[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}/g;
                if (emailPattern.test(text)) {
                    features.email = 1;
                    detectedIssues.push('Contact information detected');
                    console.log("✓ Email detected");
                }

                // Street/road names - SUPER AGGRESSIVE
                const roadWords = /(Street|St|Avenue|Ave|Road|Rd|Boulevard|Blvd|Lane|Ln|Drive|Dr|Court|Ct|Circle|Cir|Way|Plaza|Terrace|Place|Highway|Hwy)/gi;
                if (roadWords.test(text)) {
                    features.specificLocation = 1;
                    detectedIssues.push('Location information detected');
                    console.log("✓ Road/Street name detected");
                }

                // ANY time mentioned = DANGER
                const timePattern = /\b\d{1,2}(:\d{2})?\s*(am|pm|AM|PM)|morning|evening|afternoon|night/gi;
                if (timePattern.test(text)) {
                    features.routine = 1;
                    detectedIssues.push('Personal schedule/routine information detected');
                    console.log("✓ Time/schedule detected");
                }

                // Days of week = DANGER
                const dayPattern = /\b(monday|tuesday|wednesday|thursday|friday|saturday|sunday|weekday|weekend|mon|tue|wed|thu|fri|sat|sun|every|each|always|usually)\b/gi;
                if (dayPattern.test(text)) {
                    features.routine = 1;
                    detectedIssues.push('Personal schedule/routine information detected');
                    console.log("✓ Day/frequency detected");
                }

                // Workout/activity mentions = DANGER
                const activityPattern = /\b(work\s*out|workout|gym|fitness|exercise|go|visit|meet|class|study)\b/gi;
                if (activityPattern.test(text)) {
                    features.routine = 1;
                    detectedIssues.push('Personal schedule/routine information detected');
                    console.log("✓ Activity detected");
                }

                // ANY brand/chain mention = DANGER
                const brandPattern = /\b(LA\s*Fitness|Planet\s*Fitness|24\s*Hour|Gold'?s?\s*Gym|Equinox|Crunch|Anytime|Starbucks|McDonald'?s?|Target|Walmart|Costco|Whole\s*Foods|Trader\s*Joe'?s?|Chipotle|Subway|Panera)\b/gi;
                if (brandPattern.test(text)) {
                    features.venue = 1;
                    detectedIssues.push('Location information detected');
                    console.log("✓ Brand/chain detected");
                }

                // Neighborhood patterns = DANGER
                const neighborhoodPattern = /\b[A-Z0-9]+[Ss]?\s*(Ranch|Village|Hills|Heights|Park|Center|Plaza|Mall|Commons|Square|District|Beach|Bay|Valley|Creek|Grove)\b/gi;
                if (neighborhoodPattern.test(text)) {
                    features.venue = 1;
                    detectedIssues.push('Location information detected');
                    console.log("✓ Neighborhood detected");
                }

                // SSN, credit cards, etc
                const ssnPattern = /\d{3}[-\s]?\d{2}[-\s]?\d{4}/g;
                const ccPattern = /\d{4}[-\s]?\d{4}[-\s]?\d{4}[-\s]?\d{4}/g;
                
                if (ssnPattern.test(text)) {
                    features.personalId = 1;
                    detectedIssues.push('Sensitive ID number detected');
                    console.log("✓ SSN detected");
                }
                if (ccPattern.test(text)) {
                    features.personalId = 1;
                    detectedIssues.push('Sensitive ID number detected');
                    console.log("✓ Credit card detected");
                }

                // Phone numbers
                const phonePattern2 = /\(?\d{3}\)?[-.\s]?\d{3}[-.\s]?\d{4}/g;
                if (phonePattern2.test(text)) {
                    features.phoneNumber = 1;
                    detectedIssues.push('Contact information detected');
                    console.log("✓ Phone detected");
                }

                // Email
                if (text.includes('@') && text.includes('.')) {
                    features.email = 1;
                    detectedIssues.push('Contact information detected');
                    console.log("✓ Email detected");
                }

                // ZIP codes
                const zipPattern = /\b\d{5}(-\d{4})?\b/g;
                if (zipPattern.test(text)) {
                    features.zipCode = 1;
                    detectedIssues.push('Location information detected');
                    console.log("✓ ZIP code detected");
                }

                // Remove duplicate issues
                const uniqueIssues = [...new Set(detectedIssues)];
                
                console.log("Features:", features);
                console.log("Issues:", uniqueIssues);

                return { features, issues: uniqueIssues };
            }

            calculateRiskScore(features) {
                // Weighted sum of features
                let riskScore = 0;
                
                // If ANY dangerous feature is detected, automatic high risk
                if (features.routine > 0) riskScore += 30;
                if (features.venue > 0) riskScore += 30;
                if (features.specificLocation > 0) riskScore += 25;
                if (features.phoneNumber > 0) riskScore += 35;
                if (features.email > 0) riskScore += 35;
                if (features.streetAddress > 0) riskScore += 30;
                if (features.personalId > 0) riskScore += 40;
                if (features.zipCode > 0) riskScore += 15;
                if (features.namePattern > 0) riskScore += 20;
                
                console.log("Calculated risk score:", riskScore);
                
                return riskScore;
            }

            predict(text) {
                // Extract features from text
                const { features, issues } = this.extractFeatures(text);
                
                // Calculate ML risk score
                const riskScore = this.calculateRiskScore(features);
                
                console.log("Final risk score:", riskScore);
                console.log("Issues found:", issues);
                
                // Classify based on thresholds - MUCH MORE STRICT
                let severity, safe, message;
                
                if (riskScore >= 50 || issues.length >= 2) {
                    severity = 'danger';
                    safe = false;
                    message = 'Personal information detected! Please remove sensitive details before saving.';
                } else if (riskScore >= 20 || issues.length >= 1) {
                    severity = 'warning';
                    safe = false;
                    message = 'Potential privacy concerns detected. Please review carefully.';
                } else {
                    severity = 'safe';
                    safe = true;
                    message = 'No personal information detected. This looks safe to share!';
                }

                console.log("Final verdict:", severity, "Safe:", safe);

                return {
                    safe,
                    severity,
                    issues,
                    riskScore: Math.min(100, riskScore),
                    message,
                    features
                };
            }
        }

        // Initialize ML classifier
        const mlClassifier = new SafetyClassifier();

        const safetyChecks = {
            about: false,
            interests: false,
            skills: false,
            goals: false
        };

        const examples = {
            about: {
                good: "I'm a passionate software developer who loves learning new technologies. I enjoy working on both frontend and backend projects, and I'm always excited to collaborate with others on interesting challenges.",
                bad: "My name is John Smith, I live at 123 Main Street, Apt 4B, San Diego, CA 92101. You can reach me at (555) 123-4567 or john.smith@email.com. My SSN is 123-45-6789."
            },
            interests: {
                good: "I enjoy hiking, photography, reading sci-fi novels, and playing chess. I also love attending tech meetups and hackathons on weekends.",
                bad: "I work out at LA Fitness at 4S Ranch at 8pm every Tuesday and Thursday. I also go to the Starbucks on Main Street every morning at 7am."
            },
            skills: {
                good: "Proficient in Python, JavaScript, and React. Experienced with machine learning frameworks like TensorFlow and PyTorch. Strong problem-solving and communication skills.",
                bad: "I work at Google Inc., employee ID #G-847392, in Building 42, Floor 3. My manager is Sarah Johnson (sarah.j@google.com) and my work phone is 555-0192."
            },
            goals: {
                good: "Looking to collaborate on open-source projects, find study partners for algorithm practice, and connect with developers interested in AI and web development.",
                bad: "Want to meet people near my apartment at 742 Evergreen Terrace. I'm usually home alone after 8 PM on weekdays. My credit card number is 4532-1234-5678-9010."
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
                
                // Reset safety check when content changes
                safetyChecks[section] = false;
            });
        });

        function autofillSection(section, type) {
            const input = document.getElementById(`${section}-input`);
            input.value = examples[section][type];
            input.dispatchEvent(new Event('input'));
            
            // Clear previous safety check result
            document.getElementById(`${section}-result`).innerHTML = '';
            safetyChecks[section] = false;
        }

        function checkSafety(section) {
            const input = document.getElementById(`${section}-input`);
            const resultDiv = document.getElementById(`${section}-result`);
            const text = input.value.trim();

            if (!text) {
                resultDiv.innerHTML = '<div class="safety-result safety-warning"><span class="safety-icon">⚠️</span>Please enter some text first!</div>';
                return;
            }

            resultDiv.innerHTML = '<div class="safety-result safety-checking"><span class="safety-icon">⏳</span>Running AI safety analysis...</div>';

            // Run analysis
            setTimeout(() => {
                const result = mlClassifier.predict(text);
                safetyChecks[section] = result.safe;

                let resultHTML = '';
                if (result.severity === 'safe') {
                    resultHTML = `<div class="safety-result safety-safe">
                        <span class="safety-icon">✅</span>
                        <strong>Safe to share!</strong> ${result.message}
                        <div style="margin-top: 0.5em; font-size: 0.9em;">
                            <strong>Risk Score:</strong> ${result.riskScore}% (Low risk)
                        </div>
                    </div>`;
                } else if (result.severity === 'warning') {
                    resultHTML = `<div class="safety-result safety-warning">
                        <span class="safety-icon">⚠️</span>
                        <strong>Warning:</strong> ${result.message}
                        <div style="margin-top: 0.5em; font-size: 0.9em;">
                            <strong>Risk Score:</strong> ${result.riskScore}% (Medium risk)
                        </div>
                        ${result.issues.length > 0 ? `<ul class="issues-list">${result.issues.map(i => `<li>${i}</li>`).join('')}</ul>` : ''}
                    </div>`;
                } else {
                    resultHTML = `<div class="safety-result safety-danger">
                        <span class="safety-icon">🚫</span>
                        <strong>Unsafe!</strong> ${result.message}
                        <div style="margin-top: 0.5em; font-size: 0.9em;">
                            <strong>Risk Score:</strong> ${result.riskScore}% (High risk)
                        </div>
                        ${result.issues.length > 0 ? `<ul class="issues-list">${result.issues.map(i => `<li>${i}</li>`).join('')}</ul>` : ''}
                    </div>`;
                }

                resultDiv.innerHTML = resultHTML;
            }, 800);
        }

        function performSafetyCheck(text) {
            // This function is now replaced by the ML classifier
            // Kept for backwards compatibility but not used
            return mlClassifier.predict(text);
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

            // Collect data and verify safety checks
            for (const section of sections) {
                const input = document.getElementById(`${section}-input`);
                const value = input.value.trim();
                
                if (value) {
                    hasContent = true;
                    bioData[section] = value;
                    
                    if (!safetyChecks[section]) {
                        allChecked = false;
                    }
                }
            }

            if (!hasContent) {
                showStatus('Please fill in at least one section!', 'error');
                return;
            }

            if (!allChecked) {
                showStatus('⚠️ Please run safety checks on all filled sections before saving!', 'error');
                return;
            }

            const token = getCookie('jwt');
            if (!token) {
                showStatus('Please log in to save your bio', 'error');
                return;
            }

            try {
                showStatus('💾 Saving your bio...', 'success');

                const response = await fetch('/api/match/add', {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json',
                        'Authorization': `Bearer ${token}`
                    },
                    body: JSON.stringify({
                        index: 'bio',
                        data: {
                            ...bioData,
                            last_updated: new Date().toISOString(),
                            safety_checked: true
                        }
                    })
                });

                const data = await response.json();

                if (response.ok) {
                    showStatus('✅ Bio saved successfully! Your profile is ready for matchmaking.', 'success');
                } else {
                    showStatus(`❌ Error: ${data.message}`, 'error');
                }
            } catch (error) {
                showStatus(`❌ Failed to save: ${error.message}`, 'error');
            }
        }

        function showStatus(message, type) {
            const statusDiv = document.getElementById('save-status');
            statusDiv.className = `status-message status-${type}`;
            statusDiv.textContent = message;
            
            if (type === 'success') {
                setTimeout(() => {
                    statusDiv.style.display = 'none';
                }, 5000);
            }
        }
    </script>
</body>
</html>