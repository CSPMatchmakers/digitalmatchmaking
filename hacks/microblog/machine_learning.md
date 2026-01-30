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
            background: linear-gradient(135deg, #0f2027 0%, #203a43 50%, #2c5364 100%);
            margin: 0;
            padding: 1em 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        * {
            box-sizing: border-box;
        }

        .container {
            max-width: 800px;
            width: 95%;
            background: #2d3748;
            border-radius: 20px;
            padding: 1.5em;
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
        }

        .header {
            text-align: center;
            margin-bottom: 1em;
        }

        .header h1 {
            font-size: 2em;
            color: #667eea;
            margin-bottom: 0.3em;
        }

        .header p {
            color: #d1d5db;
            font-size: 0.95em;
        }

        .progress-bar {
            width: 100%;
            height: 8px;
            background: #374151;
            border-radius: 10px;
            margin-bottom: 1.2em;
            overflow: hidden;
        }

        .progress-fill {
            height: 100%;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            transition: width 0.5s ease;
            border-radius: 10px;
        }

        .progress-text {
            text-align: center;
            color: #9ca3af;
            font-size: 1em;
            margin-bottom: 0.8em;
        }

        .bio-section {
            background: #374151;
            border-radius: 12px;
            padding: 1em;
            border: 2px solid #4b5563;
            transition: all 0.3s ease;
            display: none;
        }

        .bio-section.active {
            display: block;
            animation: slideIn 0.5s ease;
        }

        .section-header {
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin-bottom: 1em;
        }

        .section-title {
            font-size: 1.6em;
            color: #f3f4f6;
            font-weight: 600;
            display: flex;
            align-items: center;
            gap: 0.5em;
        }

        .section-icon {
            font-size: 1.2em;
        }

        .autofill-buttons {
            display: flex;
            gap: 0.8em;
        }

        .autofill-btn {
            padding: 0.6em 1.3em;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-size: 0.95em;
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
            margin-bottom: 1.2em;
        }

        .madlib-template {
            background: #1f2937;
            padding: 1.2em;
            border-radius: 10px;
            margin-bottom: 1em;
            line-height: 2;
        }

        .madlib-template p {
            color: #f3f4f6;
            font-size: 1.05em;
            margin: 0;
        }

        .madlib-input {
            background: #374151;
            border: 2px solid #4b5563;
            border-radius: 6px;
            padding: 0.4em 0.8em;
            color: #667eea;
            font-size: 1em;
            font-weight: 600;
            transition: all 0.3s ease;
            min-width: 140px;
        }

        .madlib-input:focus {
            outline: none;
            border-color: #667eea;
            background: #2d3748;
            box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.1);
        }

        .madlib-input::placeholder {
            color: #9ca3af;
            font-weight: normal;
            font-style: italic;
        }

        .madlib-select {
            background: #374151;
            border: 2px solid #4b5563;
            border-radius: 6px;
            padding: 0.4em 0.8em;
            color: #667eea;
            font-size: 0.95em;
            font-weight: 600;
            transition: all 0.3s ease;
            cursor: pointer;
            min-width: 140px;
            max-width: 220px;
            display: inline-block;
        }

        .madlib-select:hover {
            border-color: #667eea;
            background: #2d3748;
        }

        .madlib-select:focus {
            outline: none;
            border-color: #667eea;
            background: #2d3748;
            box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.1);
        }

        .madlib-select option {
            background: #2d3748;
            color: #f3f4f6;
            padding: 0.5em;
        }

        .madlib-select option:first-child {
            color: #9ca3af;
            font-style: italic;
        }

        .madlib-select option.bad-option {
            color: #ef4444;
            background: #fee;
            font-weight: 600;
        }

        .bio-input {
            width: 100%;
            padding: 1em;
            border: 2px solid #4b5563;
            border-radius: 8px;
            font-size: 1.05em;
            font-family: inherit;
            resize: vertical;
            transition: all 0.3s ease;
            background: #1f2937;
            color: #f3f4f6;
            min-height: 100px;
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
            font-size: 0.9em;
            color: #9ca3af;
        }

        .button-group {
            display: flex;
            gap: 1em;
            justify-content: center;
            margin-top: 1em;
        }

        .ai-check-btn {
            padding: 1em 2.5em;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            border: none;
            border-radius: 10px;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.3s ease;
            font-size: 1.05em;
        }

        .ai-check-btn:hover:not(:disabled) {
            transform: translateY(-2px);
            box-shadow: 0 4px 15px rgba(102, 126, 234, 0.4);
        }

        .ai-check-btn:disabled {
            opacity: 0.5;
            cursor: not-allowed;
        }

        .next-btn {
            padding: 1em 2.5em;
            background: linear-gradient(135deg, #27ae60 0%, #229954 100%);
            color: white;
            border: none;
            border-radius: 10px;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.3s ease;
            font-size: 1.05em;
            display: none;
        }

        .next-btn.visible {
            display: inline-block;
        }

        .next-btn:hover:not(:disabled) {
            transform: translateY(-2px);
            box-shadow: 0 4px 15px rgba(39, 174, 96, 0.4);
        }

        .next-btn:disabled {
            opacity: 0.5;
            cursor: not-allowed;
        }

        .safety-result {
            margin-top: 1em;
            padding: 1em;
            border-radius: 10px;
            animation: slideIn 0.3s ease;
            color: #1f2937 !important;
            font-size: 1.05em;
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
            font-size: 1.3em;
            margin-right: 0.5em;
        }

        .issues-list {
            margin-top: 1em;
            padding-left: 1.8em;
            color: #1f2937 !important;
        }

        .issues-list li {
            margin-bottom: 0.4em;
            color: #1f2937 !important;
        }

        .suggestions-list {
            margin-top: 1em;
            padding-left: 1.8em;
            color: #1f2937 !important;
        }

        .suggestions-list li {
            margin-bottom: 0.4em;
            color: #1f2937 !important;
        }

        .submit-section {
            display: none;
            text-align: center;
            animation: slideIn 0.5s ease;
        }

        .submit-section.visible {
            display: block;
        }

        .submit-btn {
            padding: 1em 2.5em;
            background: linear-gradient(135deg, #27ae60 0%, #229954 100%);
            color: white;
            border: none;
            border-radius: 12px;
            font-size: 1.1em;
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
            margin-top: 1.2em;
            padding: 1.2em;
            border-radius: 10px;
            animation: slideIn 0.3s ease;
            font-size: 1.05em;
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
            padding: 0.8em;
            border-radius: 8px;
            margin-bottom: 1em;
        }

        .info-box h3 {
            color: #667eea;
            margin-top: 0;
            margin-bottom: 0.3em;
            font-size: 0.95em;
        }

        .info-box p {
            color: #d1d5db;
            line-height: 1.4;
            margin: 0;
            font-size: 0.85em;
        }

        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateY(20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @media (max-width: 768px) {
            .container {
                width: 90%;
                padding: 1.5em;
            }

            .header h1 {
                font-size: 2em;
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

            .button-group {
                flex-direction: column;
            }

            .madlib-template p {
                font-size: 1em;
            }

            .madlib-select {
                max-width: 100%;
            }
        }
    }
</style>

<div class="container">
        <div class="header">
            <h1>✨ Bio Builder</h1>
            <p>Create your matchmaking profile safely</p>
        </div>

        <div class="progress-text" id="progress-text">Question 1 of 4</div>
        <div class="progress-bar">
            <div class="progress-fill" id="progress-fill" style="width: 25%;"></div>
        </div>

        <div class="info-box">
            <h3>🛡️ AI Privacy Protection</h3>
            <p>Our advanced AI system detects personal information like phone numbers, addresses, specific locations, routines, and sensitive data. Click "AI Safety Check" and pass the check to continue!</p>
        </div>

        <div class="bio-section active" data-section="about" data-question="1">
            <div class="section-header">
                <div class="section-title">
                    <span class="section-icon">👤</span>
                    About Me
                </div>
                <div class="autofill-buttons">
                    <button class="autofill-btn autofill-good" id="about-good-btn">✅ Good Example</button>
                    <button class="autofill-btn autofill-bad" id="about-bad-btn">⚠️ Bad Example</button>
                </div>
            </div>
            <div class="madlib-template">
                <p>I'm a passionate 
                    <select class="madlib-select" id="about-profession">
                        <option value="">-- select --</option>
                        <option value="software developer">software developer</option>
                        <option value="designer">designer</option>
                        <option value="student">student</option>
                        <option value="teacher">teacher</option>
                        <option value="engineer">engineer</option>
                        <option value="artist">artist</option>
                        <option value="writer">writer</option>
                        <option value="entrepreneur">entrepreneur</option>
                        <option value="researcher">researcher</option>
                        <option value="data scientist">data scientist</option>
                        <option value="John Smith at 123 Main St" class="bad-option">John Smith at 123 Main St</option>
                        <option value="employee at Google Building 42" class="bad-option">employee at Google Building 42</option>
                    </select>
                    who loves 
                    <select class="madlib-select" id="about-hobby1">
                        <option value="">-- select --</option>
                        <option value="learning new technologies">learning new technologies</option>
                        <option value="solving problems">solving problems</option>
                        <option value="creating art">creating art</option>
                        <option value="reading books">reading books</option>
                        <option value="exploring ideas">exploring ideas</option>
                        <option value="building things">building things</option>
                        <option value="helping others">helping others</option>
                        <option value="discovering new things">discovering new things</option>
                        <option value="going to LA Fitness on Tuesdays" class="bad-option">going to LA Fitness on Tuesdays</option>
                        <option value="visiting 742 Evergreen Terrace" class="bad-option">visiting 742 Evergreen Terrace</option>
                    </select>
                    and 
                    <select class="madlib-select" id="about-hobby2">
                        <option value="">-- select --</option>
                        <option value="building innovative solutions">building innovative solutions</option>
                        <option value="creative expression">creative expression</option>
                        <option value="tackling challenges">tackling challenges</option>
                        <option value="meeting new people">meeting new people</option>
                        <option value="trying new experiences">trying new experiences</option>
                        <option value="making a difference">making a difference</option>
                        <option value="continuous learning">continuous learning</option>
                        <option value="visiting Starbucks at 7am daily" class="bad-option">visiting Starbucks at 7am daily</option>
                        <option value="sharing my phone (555) 123-4567" class="bad-option">sharing my phone (555) 123-4567</option>
                    </select>
                    . I enjoy 
                    <select class="madlib-select" id="about-activity">
                        <option value="">-- select --</option>
                        <option value="collaborating with teams">collaborating with teams</option>
                        <option value="working independently">working independently</option>
                        <option value="mentoring others">mentoring others</option>
                        <option value="exploring new ideas">exploring new ideas</option>
                        <option value="creative problem solving">creative problem solving</option>
                        <option value="deep focused work">deep focused work</option>
                        <option value="brainstorming sessions">brainstorming sessions</option>
                        <option value="calling (555) 123-4567" class="bad-option">calling (555) 123-4567</option>
                        <option value="being home alone after 8pm" class="bad-option">being home alone after 8pm</option>
                    </select>
                    and believe in 
                    <select class="madlib-select" id="about-value">
                        <option value="">-- select --</option>
                        <option value="continuous improvement">continuous improvement</option>
                        <option value="lifelong learning">lifelong learning</option>
                        <option value="creativity and innovation">creativity and innovation</option>
                        <option value="making an impact">making an impact</option>
                        <option value="collaboration">collaboration</option>
                        <option value="authenticity">authenticity</option>
                        <option value="perseverance">perseverance</option>
                        <option value="my SSN 123-45-6789" class="bad-option">my SSN 123-45-6789</option>
                        <option value="my email john.smith@email.com" class="bad-option">my email john.smith@email.com</option>
                    </select>
                    .</p>
            </div>
            <div id="about-result"></div>
            <div class="button-group">
                <button class="ai-check-btn" id="about-check-btn">🤖 AI Safety Check</button>
                <button class="next-btn" id="about-next">Next Question →</button>
            </div>
        </div>

        <div class="bio-section" data-section="interests" data-question="2">
            <div class="section-header">
                <div class="section-title">
                    <span class="section-icon">🎯</span>
                    Interests & Hobbies
                </div>
                <div class="autofill-buttons">
                    <button class="autofill-btn autofill-good" id="interests-good-btn">✅ Good Example</button>
                    <button class="autofill-btn autofill-bad" id="interests-bad-btn">⚠️ Bad Example</button>
                </div>
            </div>
            <div class="madlib-template">
                <p>In my free time, I enjoy 
                    <select class="madlib-select" id="interests-hobby1">
                        <option value="">-- select --</option>
                        <option value="hiking in nature">hiking in nature</option>
                        <option value="photography">photography</option>
                        <option value="playing music">playing music</option>
                        <option value="cooking">cooking</option>
                        <option value="gaming">gaming</option>
                        <option value="reading">reading</option>
                        <option value="exercising">exercising</option>
                        <option value="drawing">drawing</option>
                        <option value="traveling">traveling</option>
                        <option value="working out at Mira Mesa Blvd gym" class="bad-option">working out at Mira Mesa Blvd gym</option>
                        <option value="going to 123 Main Street" class="bad-option">going to 123 Main Street</option>
                    </select>
                    , 
                    <select class="madlib-select" id="interests-hobby2">
                        <option value="">-- select --</option>
                        <option value="watching movies">watching movies</option>
                        <option value="playing sports">playing sports</option>
                        <option value="crafting">crafting</option>
                        <option value="gardening">gardening</option>
                        <option value="writing">writing</option>
                        <option value="meditation">meditation</option>
                        <option value="cycling">cycling</option>
                        <option value="dancing">dancing</option>
                        <option value="visiting specific locations weekly" class="bad-option">visiting specific locations weekly</option>
                        <option value="going to my gym on Tuesdays at 8pm" class="bad-option">going to my gym on Tuesdays at 8pm</option>
                    </select>
                    , and 
                    <select class="madlib-select" id="interests-hobby3">
                        <option value="">-- select --</option>
                        <option value="reading science fiction">reading science fiction</option>
                        <option value="learning languages">learning languages</option>
                        <option value="volunteering">volunteering</option>
                        <option value="attending concerts">attending concerts</option>
                        <option value="exploring museums">exploring museums</option>
                        <option value="playing board games">playing board games</option>
                        <option value="practicing yoga">practicing yoga</option>
                        <option value="being home alone after 8pm" class="bad-option">being home alone after 8pm</option>
                        <option value="my daily routine at specific times" class="bad-option">my daily routine at specific times</option>
                    </select>
                    . I'm also interested in learning more about 
                    <select class="madlib-select" id="interests-topic">
                        <option value="">-- select --</option>
                        <option value="artificial intelligence">artificial intelligence</option>
                        <option value="sustainability">sustainability</option>
                        <option value="psychology">psychology</option>
                        <option value="space exploration">space exploration</option>
                        <option value="history">history</option>
                        <option value="philosophy">philosophy</option>
                        <option value="technology">technology</option>
                        <option value="art and design">art and design</option>
                        <option value="health and wellness">health and wellness</option>
                        <option value="my home address and routine" class="bad-option">my home address and routine</option>
                        <option value="where I live specifically" class="bad-option">where I live specifically</option>
                    </select>
                    .</p>
            </div>
            <div id="interests-result"></div>
            <div class="button-group">
                <button class="ai-check-btn" id="interests-check-btn">🤖 AI Safety Check</button>
                <button class="next-btn" id="interests-next">Next Question →</button>
            </div>
        </div>

        <div class="bio-section" data-section="skills" data-question="3">
            <div class="section-header">
                <div class="section-title">
                    <span class="section-icon">💻</span>
                    Skills & Expertise
                </div>
                <div class="autofill-buttons">
                    <button class="autofill-btn autofill-good" id="skills-good-btn">✅ Good Example</button>
                    <button class="autofill-btn autofill-bad" id="skills-bad-btn">⚠️ Bad Example</button>
                </div>
            </div>
            <div class="madlib-template">
                <p>I'm skilled at 
                    <select class="madlib-select" id="skills-skill1">
                        <option value="">-- select --</option>
                        <option value="Python">Python</option>
                        <option value="JavaScript">JavaScript</option>
                        <option value="graphic design">graphic design</option>
                        <option value="writing">writing</option>
                        <option value="public speaking">public speaking</option>
                        <option value="project management">project management</option>
                        <option value="data analysis">data analysis</option>
                        <option value="video editing">video editing</option>
                        <option value="photography">photography</option>
                        <option value="working at Google Building 42" class="bad-option">working at Google Building 42</option>
                        <option value="employee ID G-847392" class="bad-option">employee ID G-847392</option>
                    </select>
                    , 
                    <select class="madlib-select" id="skills-skill2">
                        <option value="">-- select --</option>
                        <option value="React">React</option>
                        <option value="UI/UX design">UI/UX design</option>
                        <option value="communication">communication</option>
                        <option value="leadership">leadership</option>
                        <option value="teaching">teaching</option>
                        <option value="problem solving">problem solving</option>
                        <option value="research">research</option>
                        <option value="marketing">marketing</option>
                        <option value="calling 555-0192" class="bad-option">calling 555-0192</option>
                        <option value="contacting my work phone" class="bad-option">contacting my work phone</option>
                    </select>
                    , and 
                    <select class="madlib-select" id="skills-skill3">
                        <option value="">-- select --</option>
                        <option value="machine learning">machine learning</option>
                        <option value="3D modeling">3D modeling</option>
                        <option value="critical thinking">critical thinking</option>
                        <option value="teamwork">teamwork</option>
                        <option value="time management">time management</option>
                        <option value="creative thinking">creative thinking</option>
                        <option value="strategic planning">strategic planning</option>
                        <option value="emailing sarah.j@company.com" class="bad-option">emailing sarah.j@company.com</option>
                        <option value="my manager's contact info" class="bad-option">my manager's contact info</option>
                    </select>
                    . I have 
                    <select class="madlib-select" id="skills-experience">
                        <option value="">-- select --</option>
                        <option value="beginner level">beginner level</option>
                        <option value="1 year">1 year</option>
                        <option value="2 years">2 years</option>
                        <option value="3 years">3 years</option>
                        <option value="5+ years">5+ years</option>
                        <option value="intermediate level">intermediate level</option>
                        <option value="advanced level">advanced level</option>
                        <option value="expert level">expert level</option>
                        <option value="manager Sarah Johnson" class="bad-option">manager Sarah Johnson</option>
                        <option value="working at specific company" class="bad-option">working at specific company</option>
                    </select>
                    of experience and enjoy 
                    <select class="madlib-select" id="skills-aspect">
                        <option value="">-- select --</option>
                        <option value="solving complex problems">solving complex problems</option>
                        <option value="creating beautiful designs">creating beautiful designs</option>
                        <option value="mentoring others">mentoring others</option>
                        <option value="learning new techniques">learning new techniques</option>
                        <option value="working on challenging projects">working on challenging projects</option>
                        <option value="collaborating with others">collaborating with others</option>
                        <option value="pushing boundaries">pushing boundaries</option>
                        <option value="sharing my employee details" class="bad-option">sharing my employee details</option>
                        <option value="giving out work contact info" class="bad-option">giving out work contact info</option>
                    </select>
                    .</p>
            </div>
            <div id="skills-result"></div>
            <div class="button-group">
                <button class="ai-check-btn" id="skills-check-btn">🤖 AI Safety Check</button>
                <button class="next-btn" id="skills-next">Next Question →</button>
            </div>
        </div>

        <div class="bio-section" data-section="goals" data-question="4">
            <div class="section-header">
                <div class="section-title">
                    <span class="section-icon">🎓</span>
                    Goals & Looking For
                </div>
                <div class="autofill-buttons">
                    <button class="autofill-btn autofill-good" id="goals-good-btn">✅ Good Example</button>
                    <button class="autofill-btn autofill-bad" id="goals-bad-btn">⚠️ Bad Example</button>
                </div>
            </div>
            <div class="madlib-template">
                <p>I'm looking to connect with people who are interested in 
                    <select class="madlib-select" id="goals-interest">
                        <option value="">-- select --</option>
                        <option value="web development">web development</option>
                        <option value="artificial intelligence">artificial intelligence</option>
                        <option value="creative projects">creative projects</option>
                        <option value="entrepreneurship">entrepreneurship</option>
                        <option value="academic research">academic research</option>
                        <option value="social impact">social impact</option>
                        <option value="the arts">the arts</option>
                        <option value="technology">technology</option>
                        <option value="learning together">learning together</option>
                        <option value="meeting near 742 Evergreen Terrace" class="bad-option">meeting near 742 Evergreen Terrace</option>
                        <option value="visiting my apartment at 92122" class="bad-option">visiting my apartment at 92122</option>
                    </select>
                    . My goal is to 
                    <select class="madlib-select" id="goals-goal">
                        <option value="">-- select --</option>
                        <option value="collaborate on open-source projects">collaborate on open-source projects</option>
                        <option value="learn new skills">learn new skills</option>
                        <option value="build meaningful projects">build meaningful projects</option>
                        <option value="share knowledge">share knowledge</option>
                        <option value="grow professionally">grow professionally</option>
                        <option value="make new connections">make new connections</option>
                        <option value="find study partners">find study partners</option>
                        <option value="start a creative venture">start a creative venture</option>
                        <option value="share my SSN 123-45-6789" class="bad-option">share my SSN 123-45-6789</option>
                        <option value="give out personal documents" class="bad-option">give out personal documents</option>
                    </select>
                    and I'd love to 
                    <select class="madlib-select" id="goals-activity">
                        <option value="">-- select --</option>
                        <option value="work on coding projects together">work on coding projects together</option>
                        <option value="brainstorm ideas">brainstorm ideas</option>
                        <option value="attend tech meetups">attend tech meetups</option>
                        <option value="exchange feedback">exchange feedback</option>
                        <option value="collaborate on creative work">collaborate on creative work</option>
                        <option value="practice and learn together">practice and learn together</option>
                        <option value="build something meaningful">build something meaningful</option>
                        <option value="meet at my apartment" class="bad-option">meet at my apartment</option>
                        <option value="share when I'm home alone" class="bad-option">share when I'm home alone</option>
                    </select>
                    .</p>
            </div>
            <div id="goals-result"></div>
            <div class="button-group">
                <button class="ai-check-btn" id="goals-check-btn">🤖 AI Safety Check</button>
                <button class="next-btn" id="goals-next">Finish →</button>
            </div>
        </div>

        <div class="submit-section" id="submit-section">
            <h2 style="color: #667eea; margin-bottom: 1em;">✅ All Questions Complete!</h2>
            <button class="submit-btn" id="save-btn">💾 Save Bio to Profile</button>
            <div id="save-status"></div>
    </div>
</div>

<script type="module">
        // Import API configuration
        import { pythonURI } from '{{ site.baseurl }}/assets/js/api/config.js';

        // Track safety checks and current question
        const safetyChecks = {
            about: false,
            interests: false,
            skills: false,
            goals: false
        };

        let currentQuestion = 1;
        const totalQuestions = 4;
        const questionOrder = ['about', 'interests', 'skills', 'goals'];

        // Examples
        const examples = {
            about: {
                good: {
                    profession: "software developer",
                    hobby1: "learning new technologies",
                    hobby2: "building innovative solutions",
                    activity: "collaborating with teams",
                    value: "continuous improvement"
                },
                bad: {
                    profession: "John Smith at 123 Main St",
                    hobby1: "going to LA Fitness on Tuesdays",
                    hobby2: "visiting Starbucks at 7am daily",
                    activity: "calling (555) 123-4567",
                    value: "my SSN 123-45-6789"
                }
            },
            interests: {
                good: {
                    hobby1: "hiking in nature",
                    hobby2: "watching movies",
                    hobby3: "reading science fiction",
                    topic: "artificial intelligence"
                },
                bad: {
                    hobby1: "working out at Mira Mesa Blvd gym",
                    hobby2: "visiting specific locations weekly",
                    hobby3: "being home alone after 8pm",
                    topic: "my home address and routine"
                }
            },
            skills: {
                good: {
                    skill1: "Python",
                    skill2: "React",
                    skill3: "machine learning",
                    experience: "3 years",
                    aspect: "solving complex problems"
                },
                bad: {
                    skill1: "working at Google Building 42",
                    skill2: "calling 555-0192",
                    skill3: "emailing sarah.j@company.com",
                    experience: "manager Sarah Johnson",
                    aspect: "sharing my employee details"
                }
            },
            goals: {
                good: {
                    interest: "web development",
                    goal: "collaborate on open-source projects",
                    activity: "work on coding projects together"
                },
                bad: {
                    interest: "meeting near 742 Evergreen Terrace",
                    goal: "share my SSN 123-45-6789",
                    activity: "meet at my apartment"
                }
            }
        };

        // Track input changes for Mad Libs dropdowns
        ['about', 'interests', 'skills', 'goals'].forEach(section => {
            const madlibSelects = document.querySelectorAll(`[data-section="${section}"] .madlib-select`);
            
            madlibSelects.forEach(select => {
                select.addEventListener('change', () => {
                    safetyChecks[section] = false;
                    document.getElementById(`${section}-next`).classList.remove('visible');
                    document.getElementById(`${section}-result`).innerHTML = '';
                });
            });
        });

        function autofillSection(section, type) {
            const exampleData = examples[section][type];
            
            // Fill in each Mad Libs input field
            Object.keys(exampleData).forEach(key => {
                const input = document.getElementById(`${section}-${key}`);
                if (input) {
                    input.value = exampleData[key];
                }
            });
            
            // Clear results and reset safety check
            document.getElementById(`${section}-result`).innerHTML = '';
            safetyChecks[section] = false;
            document.getElementById(`${section}-next`).classList.remove('visible');
        }

        function updateProgress() {
            const progressFill = document.getElementById('progress-fill');
            const progressText = document.getElementById('progress-text');
            const percentage = (currentQuestion / totalQuestions) * 100;
            progressFill.style.width = percentage + '%';
            progressText.textContent = `Question ${currentQuestion} of ${totalQuestions}`;
        }

        function nextQuestion(currentSection) {
            const currentSectionEl = document.querySelector(`[data-section="${currentSection}"]`);
            currentSectionEl.classList.remove('active');

            currentQuestion++;
            updateProgress();

            if (currentQuestion <= totalQuestions) {
                const nextSection = questionOrder[currentQuestion - 1];
                const nextSectionEl = document.querySelector(`[data-section="${nextSection}"]`);
                nextSectionEl.classList.add('active');
            } else {
                document.getElementById('submit-section').classList.add('visible');
                document.getElementById('progress-text').textContent = 'All Questions Complete!';
            }
        }

        async function checkSafetyWithAI(section) {
            const resultDiv = document.getElementById(`${section}-result`);
            
            // Collect all Mad Libs select dropdowns for this section
            const selects = document.querySelectorAll(`[data-section="${section}"] .madlib-select`);
            const values = Array.from(selects).map(select => select.value.trim());
            
            // Check if any dropdowns are not selected
            if (values.some(val => !val)) {
                resultDiv.innerHTML = '<div class="safety-result safety-warning"><span class="safety-icon">⚠️</span>Please select all options first!</div>';
                return;
            }
            
            // Combine all values into a text string
            const text = values.join(' ');

            resultDiv.innerHTML = '<div class="safety-result safety-checking"><span class="safety-icon">🤖</span>AI is analyzing for personal information<span class="loading-dots">...</span></div>';

            try {
                const response = await fetch(`${pythonURI}/api/analyze-bio-safety`, {
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
                    
                    const severityClass = {
                        'safe': 'safety-safe',
                        'warning': 'safety-warning',
                        'danger': 'safety-danger'
                    }[analysis.severity] || 'safety-safe';

                    safetyChecks[section] = (analysis.severity === 'safe');

                    let resultHTML = `<div class="safety-result ${severityClass}">`;
                    
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

                    if (analysis.issues_found && analysis.issues_found.length > 0) {
                        resultHTML += '<ul class="issues-list">';
                        analysis.issues_found.forEach(issue => {
                            resultHTML += `<li>${issue}</li>`;
                        });
                        resultHTML += '</ul>';
                    }

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

                    if (analysis.severity === 'safe') {
                        document.getElementById(`${section}-next`).classList.add('visible');
                    }
                } else {
                    throw new Error('Invalid response from AI');
                }

            } catch (error) {
                console.error('AI Safety Check Error:', error);
                resultDiv.innerHTML = '<div class="safety-result safety-warning"><span class="safety-icon">⚠️</span>AI analysis unavailable. Using basic safety check...</div>';
                
                safetyChecks[section] = true;
                document.getElementById(`${section}-next`).classList.add('visible');
            }
        }

        async function saveBio() {
            const sections = ['about', 'interests', 'skills', 'goals'];
            const bioData = {};
            let hasContent = false;

            for (const section of sections) {
                // Collect all Mad Libs select dropdowns for this section
                const selects = document.querySelectorAll(`[data-section="${section}"] .madlib-select`);
                const sectionData = {};
                let sectionHasContent = false;
                
                selects.forEach(select => {
                    const value = select.value.trim();
                    if (value) {
                        sectionHasContent = true;
                        hasContent = true;
                        // Extract field name from ID (e.g., "about-profession" -> "profession")
                        const fieldName = select.id.replace(`${section}-`, '');
                        sectionData[fieldName] = value;
                    }
                });
                
                if (sectionHasContent) {
                    bioData[section] = sectionData;
                }
            }

            if (!hasContent) {
                showStatus('❌ Please fill in at least one section!', 'error');
                return;
            }

            // Check if user is logged in by calling the API
            try {
                const idResponse = await fetch(`${pythonURI}/api/id`, {
                    method: 'GET',
                    credentials: 'include'
                });

                if (!idResponse.ok) {
                    showStatus('❌ Please log in to save your bio', 'error');
                    return;
                }

                const userData = await idResponse.json();
                
                if (!userData || !userData.id) {
                    showStatus('❌ Please log in to save your bio', 'error');
                    return;
                }
            } catch (error) {
                console.error('Authentication check error:', error);
                showStatus('❌ Please log in to save your bio', 'error');
                return;
            }

            try {
                showStatus('💾 Saving your bio...', 'success');

                const response = await fetch(`${pythonURI}/api/match/add`, {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json'
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

        // Event listeners for buttons
        questionOrder.forEach(section => {
            document.getElementById(`${section}-good-btn`).addEventListener('click', () => autofillSection(section, 'good'));
            document.getElementById(`${section}-bad-btn`).addEventListener('click', () => autofillSection(section, 'bad'));
            document.getElementById(`${section}-check-btn`).addEventListener('click', () => checkSafetyWithAI(section));
            document.getElementById(`${section}-next`).addEventListener('click', () => nextQuestion(section));
        });

        document.getElementById('save-btn').addEventListener('click', saveBio);

        // Add loading dots animation
        const style = document.createElement('style');
        style.textContent = `
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
        `;
        document.head.appendChild(style);
</script>