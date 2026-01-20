---
layout: post
title: Matchmaking
permalink: /api/
author: William W
breadcrumb: false
---

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Matchmaking - Beginner's Guide</title>
    <style>
        /* Force dark mode for entire page */
        body {
            background: #0f172a !important;
            color: #e2e8f0 !important;
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, sans-serif;
            margin: 0;
            padding: 20px;
        }

        .hero-section {
            background: linear-gradient(135deg, #4338ca 0%, #6366f1 100%) !important;
            color: #e2e8f0 !important;
            padding: 3rem 2rem;
            border-radius: 12px;
            margin-bottom: 2rem;
            text-align: center;
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.3);
        }

        .hero-section h1 {
            font-size: 2.5rem;
            margin-bottom: 1rem;
            color: #ffffff !important;
        }

        .hero-section p {
            font-size: 1.2rem;
            color: #e2e8f0 !important;
        }

        #auth-check-banner {
            background: #7f1d1d !important;
            color: #fca5a5 !important;
            padding: 1.5rem;
            border-radius: 8px;
            margin-bottom: 2rem;
            text-align: center;
            border: 2px solid #dc2626;
            display: none;
        }

        #auth-check-banner h3 {
            color: #fca5a5 !important;
            margin-bottom: 0.5rem;
        }

        #auth-check-banner p {
            color: #fecaca !important;
            margin-bottom: 1rem;
        }

        #login-redirect-btn {
            display: inline-block;
            background: #dc2626 !important;
            color: white !important;
            padding: 0.75rem 1.5rem;
            border-radius: 6px;
            text-decoration: none;
            font-weight: bold;
            transition: background 0.3s;
        }

        #login-redirect-btn:hover {
            background: #991b1b !important;
        }

        /* Step Guide Styles */
        .step-guide-inner {
            background: #1e3a8a;
            border: 2px solid #3b82f6;
            border-radius: 8px;
            padding: 1.5rem;
        }

        .step-guide-inner h3 {
            color: #dbeafe !important;
            margin-bottom: 1rem;
        }

        #step-content {
            color: #bfdbfe !important;
            min-height: 120px;
        }

        #step-content h4 {
            color: #93c5fd !important;
            margin-bottom: 0.5rem;
        }

        #step-content p {
            color: #bfdbfe !important;
        }

        .step-navigation {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-top: 1.5rem;
        }

        .step-btn {
            background: #475569 !important;
            color: white !important;
            padding: 0.5rem 1.5rem;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            font-weight: bold;
            transition: background 0.3s;
        }

        .step-btn:hover:not(:disabled) {
            background: #334155 !important;
        }

        .step-btn:disabled {
            opacity: 0.5;
            cursor: not-allowed;
        }

        .step-btn.next {
            background: #3b82f6 !important;
        }

        .step-btn.next:hover:not(:disabled) {
            background: #2563eb !important;
        }

        .step-indicator {
            color: #93c5fd !important;
            font-weight: bold;
        }

        /* API Tester Styles */
        .api-tester-container {
            max-width: 1200px;
            margin: 2rem auto;
            padding: 1.5rem;
            background: #1a1a2e !important;
            border-radius: 0.5rem;
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.3);
        }
        
        .api-tester-header {
            background: #16213e !important;
            border-radius: 0.5rem;
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.3);
            padding: 1.5rem;
            margin-bottom: 1.5rem;
            border: 1px solid #2d3748;
        }
        
        .header-title {
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin-bottom: 1.5rem;
            flex-wrap: wrap;
            gap: 1rem;
        }
        
        .header-title h2 {
            font-size: 1.875rem;
            font-weight: bold;
            color: #e2e8f0 !important;
            display: flex;
            align-items: center;
            gap: 0.5rem;
            margin: 0;
        }
        
        .auth-badge {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            font-size: 0.875rem;
            color: #fbbf24 !important;
            background: #422006 !important;
            padding: 0.5rem 1rem;
            border-radius: 0.5rem;
            border: 1px solid #92400e;
        }
        
        .examples-section {
            margin-bottom: 1.5rem;
        }
        
        .examples-section h3 {
            font-size: 0.875rem;
            font-weight: 600;
            color: #cbd5e1 !important;
            margin-bottom: 0.5rem;
        }
        
        .examples-buttons {
            display: flex;
            flex-wrap: wrap;
            gap: 0.5rem;
        }
        
        .example-btn {
            font-size: 0.75rem;
            padding: 0.25rem 0.75rem;
            border-radius: 0.375rem;
            border: none;
            cursor: pointer;
            transition: all 0.2s;
            font-weight: 600;
        }
        
        .example-btn.get {
            background: #1e40af !important;
            color: #dbeafe !important;
        }
        
        .example-btn.get:hover {
            background: #1e3a8a !important;
        }
        
        .example-btn.post {
            background: #065f46 !important;
            color: #d1fae5 !important;
        }
        
        .example-btn.post:hover {
            background: #064e3b !important;
        }
        
        .request-section {
            margin-bottom: 1rem;
        }
        
        .request-label {
            display: block;
            font-size: 0.875rem;
            font-weight: 600;
            color: #cbd5e1 !important;
            margin-bottom: 0.5rem;
        }
        
        .request-controls {
            display: flex;
            gap: 0.5rem;
            flex-wrap: wrap;
        }
        
        .method-select {
            padding: 0.5rem 1rem;
            border: 2px solid #4a5568 !important;
            border-radius: 0.5rem;
            font-weight: 600;
            font-size: 1rem;
            background: #2d3748 !important;
            color: #e2e8f0 !important;
            cursor: pointer;
        }
        
        .method-select:focus {
            outline: none;
            border-color: #3b82f6 !important;
            box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.3);
        }
        
        .url-input {
            flex: 1;
            min-width: 300px;
            padding: 0.5rem 1rem;
            border: 2px solid #4a5568 !important;
            border-radius: 0.5rem;
            font-size: 1rem;
            background: #2d3748 !important;
            color: #e2e8f0 !important;
        }
        
        .url-input:focus {
            outline: none;
            border-color: #3b82f6 !important;
            box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.3);
        }
        
        .send-btn {
            padding: 0.5rem 1.5rem;
            border: none;
            border-radius: 0.5rem;
            font-weight: 600;
            color: #ffffff !important;
            cursor: pointer;
            transition: all 0.2s;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }
        
        .send-btn.GET {
            background: #3b82f6 !important;
        }
        
        .send-btn.GET:hover {
            background: #2563eb !important;
        }
        
        .send-btn.POST {
            background: #10b981 !important;
        }
        
        .send-btn.POST:hover {
            background: #059669 !important;
        }
        
        .send-btn:disabled {
            opacity: 0.5;
            cursor: not-allowed;
        }
        
        .clear-btn {
            padding: 0.5rem 1rem;
            background: #64748b !important;
            color: #ffffff !important;
            border: none;
            border-radius: 0.5rem;
            cursor: pointer;
            transition: all 0.2s;
        }
        
        .clear-btn:hover {
            background: #475569 !important;
        }
        
        .body-section {
            margin-top: 1rem;
        }
        
        .body-textarea {
            width: 100%;
            height: 160px;
            padding: 1rem;
            border: 2px solid #4a5568 !important;
            border-radius: 0.5rem;
            font-family: 'Courier New', monospace;
            font-size: 0.875rem;
            background: #2d3748 !important;
            color: #e2e8f0 !important;
            resize: vertical;
        }
        
        .body-textarea:focus {
            outline: none;
            border-color: #3b82f6 !important;
            box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.3);
        }
        
        .response-container {
            background: #16213e !important;
            border-radius: 0.5rem;
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.3);
            padding: 1.5rem;
            margin-bottom: 1.5rem;
            border: 1px solid #2d3748;
        }
        
        .response-header {
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin-bottom: 1rem;
        }
        
        .response-header h3 {
            font-size: 1.125rem;
            font-weight: 600;
            color: #e2e8f0 !important;
            margin: 0;
        }
        
        .status-badge {
            padding: 0.25rem 1rem;
            border-radius: 9999px;
            font-size: 0.875rem;
            font-weight: 600;
        }
        
        .status-badge.success {
            color: #6ee7b7 !important;
            background: #064e3b !important;
            border: 1px solid #059669;
        }
        
        .status-badge.error {
            color: #fca5a5 !important;
            background: #7f1d1d !important;
            border: 1px solid #dc2626;
        }
        
        .status-badge.auth {
            color: #fcd34d !important;
            background: #422006 !important;
            border: 1px solid #ca8a04;
        }
        
        .response-content {
            background: #0f172a !important;
            color: #cbd5e1 !important;
            padding: 1rem;
            border-radius: 0.5rem;
            overflow-x: auto;
            font-family: 'Courier New', monospace;
            font-size: 0.875rem;
            max-height: 400px;
            overflow-y: auto;
            white-space: pre-wrap;
            border: 1px solid #1e293b;
        }
        
        .tips-section {
            background: #1e3a8a !important;
            border: 1px solid #2563eb;
            border-radius: 0.5rem;
            padding: 1rem;
            margin-top: 1.5rem;
        }
        
        .tips-section h4 {
            font-weight: 600;
            color: #dbeafe !important;
            margin-bottom: 0.5rem;
        }
        
        .tips-section ul {
            font-size: 0.875rem;
            color: #bfdbfe !important;
            list-style: none;
            padding: 0;
            margin: 0;
        }
        
        .tips-section li {
            margin-bottom: 0.25rem;
        }

        /* Collapsible Section Styles */
        .collapsible-section {
            background: #1e293b !important;
            border-radius: 12px;
            margin-bottom: 1rem;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.3);
            border: 1px solid #334155;
            overflow: hidden;
        }

        .collapsible-header {
            background: linear-gradient(135deg, #334155 0%, #475569 100%);
            padding: 1.5rem;
            cursor: pointer;
            display: flex;
            justify-content: space-between;
            align-items: center;
            transition: background 0.3s;
        }

        .collapsible-header:hover {
            background: linear-gradient(135deg, #475569 0%, #64748b 100%);
        }

        .collapsible-header h2 {
            color: #e2e8f0 !important;
            margin: 0;
            font-size: 1.5rem;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        .collapsible-icon {
            font-size: 1.5rem;
            transition: transform 0.3s;
            color: #94a3b8;
        }

        .collapsible-icon.open {
            transform: rotate(180deg);
        }

        .collapsible-content {
            max-height: 0;
            overflow: hidden;
            transition: max-height 0.3s ease-out;
            padding: 0 1.5rem;
        }

        .collapsible-content.open {
            max-height: 5000px;
            padding: 1.5rem;
            transition: max-height 0.5s ease-in;
        }

        .section-card {
            background: transparent !important;
            padding: 0;
            margin: 0;
            border: none;
            box-shadow: none;
        }

        .section-card p, .section-card li, .section-card em, .section-card strong {
            color: #cbd5e1 !important;
        }

        .info-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 1.5rem;
            margin-top: 1.5rem;
        }

        .info-box {
            background: linear-gradient(135deg, #4338ca 0%, #6366f1 100%) !important;
            color: #ffffff !important;
            padding: 1.5rem;
            border-radius: 8px;
            transition: transform 0.3s ease;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.3);
        }

        .info-box:hover {
            transform: translateY(-5px);
        }

        .info-box h3 {
            font-size: 1.2rem;
            margin-bottom: 0.5rem;
            color: #ffffff !important;
        }

        .info-box p {
            font-size: 0.95rem;
            line-height: 1.5;
            color: #e2e8f0 !important;
        }

        code {
            background: #0f172a !important;
            color: #cbd5e1 !important;
            padding: 0.25rem 0.5rem !important;
            border-radius: 4px !important;
            font-family: 'Courier New', monospace;
            border: 1px solid #1e293b;
            font-size: 0.9em !important;
        }

        pre code {
            display: block !important;
            padding: 1.5rem !important;
            margin: 1rem 0 !important;
            border-radius: 8px !important;
            overflow-x: auto;
        }

        .step-card {
            background: #334155 !important;
            border-left: 4px solid #6366f1;
            padding: 1.5rem;
            margin-bottom: 1.5rem;
            border-radius: 0 8px 8px 0;
            color: #e2e8f0 !important;
        }

        .step-card h4 {
            color: #818cf8 !important;
            margin-bottom: 0.5rem;
        }

        .step-card p, .step-card em {
            color: #cbd5e1 !important;
        }

        .tips-banner {
            background: #1e3a8a !important;
            border: 2px solid #3b82f6;
            border-radius: 8px;
            padding: 1rem 1.5rem;
            margin: 1.5rem 0;
            color: #bfdbfe !important;
        }

        .tips-banner strong, .tips-banner code {
            color: #dbeafe !important;
        }
    </style>
</head>
<body>
    <div id="auth-check-banner">
        <h3>🔒 Authentication Required</h3>
        <p>You must be logged in to use the interactive features on this page.</p>
        <a id="login-redirect-btn" href="#">Login Now →</a>
    </div>

    <!-- Step Guide -->
    <div class="collapsible-section">
        <div class="collapsible-header" onclick="toggleSection(this)">
            <h2>📋 Quick Start Guide</h2>
            <span class="collapsible-icon">▼</span>
        </div>
        <div class="collapsible-content">
            <div class="step-guide-inner">
                <div id="step-content">
                    <!-- Step content will be inserted here by JavaScript -->
                </div>
                <div class="step-navigation">
                    <button id="prevBtn" class="step-btn" onclick="changeStep(-1)">← Previous</button>
                    <div class="step-indicator">Step <span id="currentStep">1</span> of 5</div>
                    <button id="nextBtn" class="step-btn next" onclick="changeStep(1)">Next →</button>
                </div>
            </div>
        </div>
    </div>

    <!-- API Tester -->
    <div class="api-tester-container" style="margin-top: 1rem;">
        <div class="api-tester-header">
            <div class="header-title">
                <h2>
                    <svg width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                        <line x1="22" y1="2" x2="11" y2="13"></line>
                        <polygon points="22 2 15 22 11 13 2 9 22 2"></polygon>
                    </svg>
                    Matchmaking API Tester
                </h2>
                <div class="auth-badge">
                    <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                        <rect x="3" y="11" width="18" height="11" rx="2" ry="2"></rect>
                        <path d="M7 11V7a5 5 0 0 1 10 0v4"></path>
                    </svg>
                    <span>Requires JWT Authentication</span>
                </div>
            </div>

            <div class="examples-section">
                <h3>🎯 Matchmaking API Endpoints:</h3>
                <div class="examples-buttons">
                    <button class="example-btn post" onclick="loadExample('setupProfile')">1️⃣ POST Setup Profile</button>
                    <button class="example-btn post" onclick="loadExample('addProfileData')">2️⃣ POST Add Profile Data</button>
                    <button class="example-btn get" onclick="loadExample('getProfile')">3️⃣ GET Profile Data</button>
                    <button class="example-btn post" onclick="loadExample('saveProfileJSON')">4️⃣ POST Save Profile JSON</button>
                    <button class="example-btn get" onclick="loadExample('getAllData')">5️⃣ GET All Users Data</button>
                </div>
            </div>

            <div class="request-section">
                <label class="request-label">Request</label>
                <div class="request-controls">
                    <select id="method" class="method-select">
                        <option value="GET">GET</option>
                        <option value="POST">POST</option>
                        <option value="PUT">PUT</option>
                        <option value="DELETE">DELETE</option>
                    </select>
                    
                    <input 
                        type="text" 
                        id="url" 
                        class="url-input" 
                        value=""
                        placeholder="API endpoint URL will be set automatically"
                    />
                    
                    <button id="sendBtn" class="send-btn GET" onclick="sendRequest()">
                        <span id="btnText">Send</span>
                        <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                            <line x1="22" y1="2" x2="11" y2="13"></line>
                            <polygon points="22 2 15 22 11 13 2 9 22 2"></polygon>
                        </svg>
                    </button>
                    
                    <button class="clear-btn" onclick="clearAll()">
                        <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                            <polyline points="3 6 5 6 21 6"></polyline>
                            <path d="M19 6v14a2 2 0 0 1-2 2H7a2 2 0 0 1-2-2V6m3 0V4a2 2 0 0 1 2-2h4a2 2 0 0 1 2 2v2"></path>
                        </svg>
                    </button>
                </div>
            </div>

            <div id="bodySection" class="body-section" style="display: none;">
                <label class="request-label">Request Body (JSON)</label>
                <textarea 
                    id="requestBody" 
                    class="body-textarea"
                    placeholder='{"key": "value"}'
                >{}</textarea>
            </div>
        </div>

        <div class="response-container">
            <div class="response-header">
                <h3>Response</h3>
                <span id="statusBadge" class="status-badge" style="display: none;"></span>
            </div>
            <pre id="responseContent" class="response-content">Response will appear here...</pre>
        </div>

        <div id="headersSection" class="response-container" style="display: none;">
            <div class="response-header">
                <h3>Response Headers</h3>
            </div>
            <pre id="headersContent" class="response-content"></pre>
        </div>

        <div class="collapsible-section" style="margin-top: 0;">
            <div class="collapsible-header" onclick="toggleSection(this)">
                <h2 style="font-size: 1.2rem;">💡 Tips & Info</h2>
                <span class="collapsible-icon">▼</span>
            </div>
            <div class="collapsible-content">
                <div class="tips-section" style="margin-top: 0; background: transparent !important; border: none; padding: 0;">
                    <ul>
                        <li>• Follow the numbered buttons in order for best results</li>
                        <li>• Start with "Setup Profile" to initialize your matchmaking profile (only once!)</li>
                        <li>• Use "Add Profile Data" to add individual fields like hobbies, interests, etc.</li>
                        <li>• Use "Save Profile JSON" to save multiple questions/answers at once</li>
                        <li>• Check your profile anytime with "GET Profile Data"</li>
                        <li>• Status 201 = Success (Created), 200 = Success, 404 = Not Found, 409 = Already Exists</li>
                        <li>• Your profile data is saved and will be used for matchmaking later!</li>
                    </ul>
                </div>
            </div>
        </div>
    </div>

    <!-- Collapsible Sections Below -->
    <div style="max-width: 1200px; margin: 2rem auto;">
        <!-- What is This Section -->
        <div class="collapsible-section">
            <div class="collapsible-header" onclick="toggleSection(this)">
                <h2>🤔 What is This?</h2>
                <span class="collapsible-icon">▼</span>
            </div>
            <div class="collapsible-content">
                <div class="section-card">
                    <p><strong>Matchmaking API</strong> is like a mini-Twitter backend. It's the server part of a social media app where:</p>
                    <ul>
                        <li>👥 Users can sign up and log in</li>
                        <li>📝 Users can write posts</li>
                        <li>📖 Users can read other people's posts</li>
                    </ul>
                    <p><strong>Important:</strong> This is just the backend - there's no pretty website interface. It's the "behind the scenes" code that makes everything work.</p>
                    <div class="tips-banner">
                        <strong>💡 Think of it like this:</strong><br>
                        Instagram App (Frontend) ↔️ Instagram's Servers (Backend like this!)
                    </div>
                </div>
            </div>
        </div>

        <!-- Why Should I Care Section -->
        <div class="collapsible-section">
            <div class="collapsible-header" onclick="toggleSection(this)">
                <h2>🎯 Why Should I Care?</h2>
                <span class="collapsible-icon">▼</span>
            </div>
            <div class="collapsible-content">
                <div class="section-card">
                    <div class="info-grid">
                        <div class="info-box">
                            <h3>📚 AP CSP Concepts</h3>
                            <p>Networks, data, the internet, and how apps work</p>
                        </div>
                        <div class="info-box">
                            <h3>🐍 Uses Python</h3>
                            <p>You might already know some Python!</p>
                        </div>
                        <div class="info-box">
                            <h3>👀 See it Work</h3>
                            <p>Not just theory - you can actually run it and test it</p>
                        </div>
                        <div class="info-box">
                            <h3>🌐 Real-World</h3>
                            <p>This is how actual apps like Instagram work</p>
                        </div>
                    </div>
                    <p style="margin-top: 1.5rem;"><strong>You don't need to understand all the code!</strong> The goal is to:</p>
                    <ul>
                        <li>✅ See how a backend works</li>
                        <li>✅ Try using an API</li>
                        <li>✅ Understand how data moves around</li>
                    </ul>
                </div>
            </div>
        </div>
    </div>

    <script type="module">
        // Import from config.js
        import { pythonURI, fetchOptions } from '/digitalmatchmaking/assets/js/api/config.js';

        console.log('[DEBUG] Imported pythonURI:', pythonURI);
        console.log('[DEBUG] Imported fetchOptions:', fetchOptions);

        // Check authentication by calling /api/id
        async function checkAuthentication(retries = 3, delay = 1000) {
            console.log('[DEBUG] ========================================');
            console.log('[DEBUG] Starting authentication check...');
            console.log('[DEBUG] Current URL:', window.location.href);
            console.log('[DEBUG] Current domain:', window.location.hostname);
            console.log('[DEBUG] Python URI:', pythonURI);
            console.log('[DEBUG] Will attempt', retries, 'times with', delay, 'ms delay');
            console.log('[DEBUG] ========================================');
            
            for (let attempt = 1; attempt <= retries; attempt++) {
                console.log(`[DEBUG] Authentication attempt ${attempt}/${retries}`);
                
                try {
                    const response = await fetch(`${pythonURI}/api/id`, {
                        ...fetchOptions,
                        credentials: 'include'
                    });
                    
                    console.log(`[DEBUG] Response status: ${response.status}`);
                    console.log(`[DEBUG] Response ok: ${response.ok}`);
                    
                    if (response.ok) {
                        const data = await response.json();
                        console.log('[DEBUG] ✅ Authentication SUCCESSFUL!');
                        console.log('[DEBUG] User data:', data);
                        console.log('[DEBUG] ========================================');
                        return true;
                    } else {
                        console.log(`[DEBUG] ❌ Response not OK (status: ${response.status})`);
                        
                        // If not the last attempt, wait before retrying
                        if (attempt < retries) {
                            console.log(`[DEBUG] Waiting ${delay}ms before retry...`);
                            await new Promise(resolve => setTimeout(resolve, delay));
                        }
                    }
                } catch (error) {
                    console.log(`[DEBUG] ❌ Fetch error:`, error.message);
                    
                    // If not the last attempt, wait before retrying
                    if (attempt < retries) {
                        console.log(`[DEBUG] Waiting ${delay}ms before retry...`);
                        await new Promise(resolve => setTimeout(resolve, delay));
                    }
                }
            }
            
            console.log('[DEBUG] ❌ Authentication FAILED after all attempts');
            console.log('[DEBUG] ❌ Authentication FAILED after all attempts');
            console.log('[DEBUG] ========================================');
            
            // Disable everything
            methodSelect.disabled = true;
            urlInput.disabled = true;
            requestBodyTextarea.disabled = true;
            sendBtn.disabled = true;
                
            responseContent.innerHTML = `<div style="color: #fbbf24; font-weight: bold; font-size: 1.2rem; text-align: center; padding: 2rem;">
                🔒 Authentication Required
                
                <div style="color: #cbd5e1; font-size: 0.9rem; margin-top: 1rem; font-weight: normal;">
                    You must be logged in to use the API tester.
                    
                    Please log in to your account first, then refresh this page.
                </div>
            </div>`;
            
            const exampleButtons = document.querySelectorAll('.example-btn');
            exampleButtons.forEach(btn => {
                btn.disabled = true;
                btn.style.opacity = '0.5';
                btn.style.cursor = 'not-allowed';
            });
                
            return false;
        }

        // Quick initial check (no retry needed for banner)
        async function quickAuthCheck() {
            console.log('[DEBUG] Running quick auth check for banner...');
            
            try {
                const response = await fetch(`${pythonURI}/api/id`, {
                    ...fetchOptions,
                    credentials: 'include'
                });
                
                const isAuth = response.ok;
                console.log('[DEBUG] Quick check result:', isAuth ? 'Authenticated' : 'Not authenticated');
                return isAuth;
            } catch (error) {
                console.log('[DEBUG] Quick check failed:', error.message);
                return false;
            }
        }

        // Authentication banner check (runs immediately)
        (async function() {
            console.log('[DEBUG] Running immediate banner check...');
            const isAuth = await quickAuthCheck();
            
            if (!isAuth) {
                const banner = document.getElementById('auth-check-banner');
                if (banner) {
                    console.log('[DEBUG] Showing auth banner');
                    banner.style.display = 'block';
                }
                
                const loginBtn = document.getElementById('login-redirect-btn');
                if (loginBtn) {
                    const protocol = window.location.protocol;
                    const hostname = window.location.hostname;
                    const port = window.location.port;
                    
                    let baseUrl;
                    if (hostname === 'localhost' || hostname === '127.0.0.1') {
                        baseUrl = `${protocol}//${hostname}:${port}`;
                    } else {
                        baseUrl = `${protocol}//${hostname}`;
                    }
                    
                    loginBtn.href = `${baseUrl}/digitalmatchmaking/login`;
                    console.log('[DEBUG] Login redirect URL:', loginBtn.href);
                }
            } else {
                console.log('[DEBUG] Already authenticated - no banner needed');
            }
        })();

        // Step Guide
        let currentStepIndex = 0;

        const steps = [
            {
                title: "Step 1: Initialize Your Profile",
                content: "Click <strong>\"POST Setup Profile\"</strong> to create your matchmaking profile. You should see a success message with status 201. ⚠️ <strong>Only do this once!</strong> If you already have a profile, you'll get a 409 error (profile already exists)."
            },
            {
                title: "Step 2: Add Your Information",
                content: "Click <strong>\"POST Add Profile Data\"</strong> to add information like your favorite hobbies, interests, etc. Edit the JSON body to add different data fields. You can call this multiple times to add more data."
            },
            {
                title: "Step 3: View Your Profile",
                content: "Click <strong>\"GET Profile Data\"</strong> to see all your saved information. This shows everything you've added to your profile."
            },
            {
                title: "Step 4: Save Quiz Results",
                content: "Click <strong>\"POST Save Profile JSON\"</strong> to save multiple questions and answers at once (like from a quiz or form). This is useful for bulk updates to your profile."
            },
            {
                title: "Step 5: View All Users",
                content: "Click <strong>\"GET All Users Data\"</strong> to see everyone's profile data (useful for matching algorithms and seeing what others have shared)."
            }
        ];

        function showStep(index) {
            const stepContent = document.getElementById('step-content');
            const currentStepDisplay = document.getElementById('currentStep');
            const prevBtn = document.getElementById('prevBtn');
            const nextBtn = document.getElementById('nextBtn');

            stepContent.innerHTML = `
                <h4>${steps[index].title}</h4>
                <p>${steps[index].content}</p>
            `;

            currentStepDisplay.textContent = index + 1;

            prevBtn.disabled = index === 0;
            nextBtn.disabled = index === steps.length - 1;

            prevBtn.style.opacity = index === 0 ? '0.5' : '1';
            prevBtn.style.cursor = index === 0 ? 'not-allowed' : 'pointer';

            nextBtn.style.opacity = index === steps.length - 1 ? '0.5' : '1';
            nextBtn.style.cursor = index === steps.length - 1 ? 'not-allowed' : 'pointer';
        }

        function changeStep(direction) {
            currentStepIndex += direction;
            if (currentStepIndex < 0) currentStepIndex = 0;
            if (currentStepIndex >= steps.length) currentStepIndex = steps.length - 1;
            showStep(currentStepIndex);
        }

        showStep(0);

        // Collapsible sections
        function toggleSection(header) {
            const content = header.nextElementSibling;
            const icon = header.querySelector('.collapsible-icon');
            
            content.classList.toggle('open');
            icon.classList.toggle('open');
        }

        // API Tester functionality
        const methodSelect = document.getElementById('method');
        const urlInput = document.getElementById('url');
        const requestBodyTextarea = document.getElementById('requestBody');
        const bodySection = document.getElementById('bodySection');
        const sendBtn = document.getElementById('sendBtn');
        const btnText = document.getElementById('btnText');
        const responseContent = document.getElementById('responseContent');
        const statusBadge = document.getElementById('statusBadge');
        const headersSection = document.getElementById('headersSection');
        const headersContent = document.getElementById('headersContent');

        // Set the default URL based on environment
        urlInput.value = `${pythonURI}/api/match/`;
        console.log('[DEBUG] Default URL set to:', urlInput.value);

        // Main authentication check for API tester (waits for cookie)
        let isAuthenticated = false;

        (async function() {
            console.log('[DEBUG] Starting main authentication process...');
            isAuthenticated = await checkAuthentication();
            
            console.log('[DEBUG] Final isAuthenticated value:', isAuthenticated);
            
            if (isAuthenticated) {
                // Hide the auth banner if cookie was found
                const banner = document.getElementById('auth-check-banner');
                if (banner) {
                    console.log('[DEBUG] Hiding auth banner');
                    banner.style.display = 'none';
                }
            } else {
                console.log('[DEBUG] Keeping auth banner visible');
            }
            
            console.log('[DEBUG] Authentication process complete');
        })();

        methodSelect.addEventListener('change', function() {
            if (!isAuthenticated) return;
            
            const method = this.value;
            sendBtn.className = `send-btn ${method}`;
            
            if (method === 'POST' || method === 'PUT') {
                bodySection.style.display = 'block';
            } else {
                bodySection.style.display = 'none';
            }
        });

        function loadExample(example) {
            if (!isAuthenticated) {
                alert('Please log in to use the API tester.');
                return;
            }
            
            switch(example) {
                case 'setupProfile':
                    methodSelect.value = 'POST';
                    urlInput.value = `${pythonURI}/api/match/setup`;
                    requestBodyTextarea.value = '{}';
                    break;
                case 'addProfileData':
                    methodSelect.value = 'POST';
                    urlInput.value = `${pythonURI}/api/match/add`;
                    requestBodyTextarea.value = '{\n  "index": "favorite_hobby",\n  "data": "Reading and coding"\n}';
                    break;
                case 'getProfile':
                    methodSelect.value = 'GET';
                    urlInput.value = `${pythonURI}/api/match/data`;
                    requestBodyTextarea.value = '{}';
                    break;
                case 'saveProfileJSON':
                    methodSelect.value = 'POST';
                    urlInput.value = `${pythonURI}/api/match/save-profile-json`;
                    requestBodyTextarea.value = '{\n  "profile_data": [\n    {\n      "question": "What is your favorite hobby?",\n      "response": "Reading"\n    },\n    {\n      "question": "What is your preferred study time?",\n      "response": "Morning"\n    },\n    {\n      "question": "What type of projects do you enjoy?",\n      "response": "Web development"\n    },\n    {\n      "question": "What programming language do you prefer?",\n      "response": "Python"\n    }\n  ]\n}';
                    break;
                case 'getAllData':
                    methodSelect.value = 'GET';
                    urlInput.value = `${pythonURI}/api/match/all-data`;
                    requestBodyTextarea.value = '{}';
                    break;
            }
            
            methodSelect.dispatchEvent(new Event('change'));
        }

        async function sendRequest() {
            if (!isAuthenticated) {
                alert('Please log in to use the API tester.');
                return;
            }
            
            const method = methodSelect.value;
            const url = urlInput.value;
            const requestBody = requestBodyTextarea.value;

            btnText.textContent = 'Sending...';
            sendBtn.disabled = true;
            responseContent.textContent = '';
            statusBadge.style.display = 'none';
            headersSection.style.display = 'none';

            try {
                const options = {
                    method: method,
                    mode: 'cors',
                    credentials: 'include',
                    headers: {
                        'Content-Type': 'application/json',
                        'X-Origin': 'client'
                    }
                };

                if (method === 'POST' || method === 'PUT' || method === 'DELETE') {
                    try {
                        JSON.parse(requestBody);
                        options.body = requestBody;
                    } catch (e) {
                        responseContent.textContent = 'Invalid JSON in request body';
                        btnText.textContent = 'Send';
                        sendBtn.disabled = false;
                        return;
                    }
                }

                const startTime = Date.now();
                const response = await fetch(url, options);
                const duration = Date.now() - startTime;

                statusBadge.textContent = `Status: ${response.status}`;
                statusBadge.style.display = 'inline-block';
                
                if (response.status === 401 || response.status === 403) {
                    statusBadge.className = 'status-badge auth';
                } else if (response.status >= 200 && response.status < 300) {
                    statusBadge.className = 'status-badge success';
                } else {
                    statusBadge.className = 'status-badge error';
                }

                const responseHeaders = {};
                response.headers.forEach((value, key) => {
                    responseHeaders[key] = value;
                });
                headersContent.textContent = JSON.stringify(responseHeaders, null, 2);
                headersSection.style.display = 'block';

                let data;
                const contentType = response.headers.get('content-type');
                if (contentType && contentType.includes('application/json')) {
                    data = await response.json();
                } else {
                    data = await response.text();
                }

                const responseObj = {
                    status: response.status,
                    statusText: response.statusText,
                    duration: `${duration}ms`,
                    data: data
                };

                if (response.status === 401 || response.status === 403) {
                    responseObj.authMessage = '⚠️ Authentication required. Please log in to access this endpoint.';
                }

                responseContent.textContent = JSON.stringify(responseObj, null, 2);

            } catch (error) {
                responseContent.textContent = `Error: ${error.message}\n\nPlease check:\n- Is the server running?\n- Is the URL correct?\n- Are you logged in?`;
                statusBadge.style.display = 'none';
            }

            btnText.textContent = 'Send';
            sendBtn.disabled = false;
        }

        function clearAll() {
            if (!isAuthenticated) {
                alert('Please log in to use the API tester.');
                return;
            }
            
            urlInput.value = `${pythonURI}/api/match/`;
            requestBodyTextarea.value = '{}';
            responseContent.textContent = 'Response will appear here...';
            statusBadge.style.display = 'none';
            headersSection.style.display = 'none';
        }

        // Make functions available globally since we're using module type
        window.changeStep = changeStep;
        window.toggleSection = toggleSection;
        window.loadExample = loadExample;
        window.sendRequest = sendRequest;
        window.clearAll = clearAll;
    </script>
</body>
</html>