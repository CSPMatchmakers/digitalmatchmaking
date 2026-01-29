---
layout: opencs
title: Account Port
permalink: /api/
author: William W
breadcrumb: false
---

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Account Port</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        html, body {
            width: 100%;
            height: 100%;
            background: #0d0d0d;
            color: #e4e4e7;
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Roboto', 'Oxygen', 'Ubuntu', sans-serif;
            line-height: 1.6;
        }

        /* Header */
        .header {
            background: linear-gradient(135deg, #1a1a1a 0%, #0d0d0d 100%);
            border-bottom: 1px solid #262626;
            padding: 1.5rem 2rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
            height: 70px;
        }

        .header-left {
            display: flex;
            align-items: center;
            gap: 1rem;
        }

        .header-icon {
            font-size: 1.5rem;
        }

        .header-title {
            font-size: 1.3rem;
            font-weight: 700;
            color: #fafafa;
        }

        .auth-indicator {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            padding: 0.5rem 1rem;
            background: #1a1a1a;
            border: 1px solid #262626;
            border-radius: 6px;
            font-size: 0.875rem;
        }

        .status-light {
            width: 8px;
            height: 8px;
            border-radius: 50%;
            background: #ef4444;
        }

        .status-light.active {
            background: #22c55e;
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.5; }
        }

        /* Main Container */
        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 1.5rem;
        }

        /* Sections */
        .section {
            margin-bottom: 2rem;
        }

        .section-title {
            font-size: 1.2rem;
            font-weight: 700;
            color: #fafafa;
            margin-bottom: 1rem;
            padding-bottom: 0.5rem;
            border-bottom: 2px solid #262626;
        }

        /* Help Sidebar */
        .help-sidebar {
            display: flex;
            flex-direction: column;
            gap: 1rem;
            margin-top: 1.5rem;
        }

        .card {
            background: transparent;
            border: none;
            padding: 0;
        }

        .card-title {
            font-size: 0.9rem;
            font-weight: 600;
            color: #3b82f6;
            text-transform: uppercase;
            letter-spacing: 0.05em;
            margin-bottom: 0.6rem;
        }

        /* Quick Actions */
        .action-btn {
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
            padding: 0.6rem 1rem;
            background: #1a1a1a;
            border: 1px solid #3b82f6;
            border-radius: 6px;
            cursor: pointer;
            transition: all 0.2s ease;
            color: #e4e4e7;
            text-decoration: none;
            margin-right: 0.8rem;
            margin-bottom: 0.8rem;
            font-size: 0.9rem;
            font-weight: 500;
            user-select: none;
        }

        .action-btn:hover {
            background: #3b82f6;
            color: #0d0d0d;
        }

        .action-icon {
            font-size: 1.1rem;
        }

        /* Status Card */
        .status-card {
            background: #0d0d0d;
            border: 1px solid #262626;
            border-radius: 6px;
            padding: 1.5rem 1rem;
            text-align: center;
        }

        .status-icon {
            font-size: 2.5rem;
            margin-bottom: 0.75rem;
        }

        .status-label {
            color: #a1a1aa;
            font-size: 0.875rem;
        }

        /* Center Column - Request/Response */
        .main-content {
            display: flex;
            flex-direction: column;
            gap: 1.5rem;
        }

        .request-section {
            background: #1a1a1a;
            border: 1px solid #262626;
            border-radius: 8px;
            overflow: hidden;
        }

        .request-controls {
            padding: 1rem 1.25rem;
            border-bottom: 1px solid #262626;
            display: flex;
            gap: 0.6rem;
            flex-wrap: wrap;
            background: #141414;
        }

        .method-select {
            padding: 0.5rem 0.75rem;
            background: #0d0d0d;
            border: 1px solid #262626;
            border-radius: 4px;
            color: #3b82f6;
            font-weight: 600;
            font-size: 0.875rem;
            cursor: pointer;
            flex-shrink: 0;
            min-width: 75px;
        }

        .method-select:focus {
            outline: none;
            border-color: #3b82f6;
            box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.1);
        }

        .url-input-group {
            flex: 1;
            display: flex;
            gap: 0.75rem;
            min-width: 200px;
        }

        .url-input {
            flex: 1;
            padding: 0.5rem 0.75rem;
            background: #0d0d0d;
            border: 1px solid #262626;
            border-radius: 4px;
            color: #e4e4e7;
            font-size: 0.875rem;
            font-family: 'Monaco', 'Courier New', monospace;
        }

        .url-input:focus {
            outline: none;
            border-color: #3b82f6;
            box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.1);
        }

        .send-btn {
            padding: 0.5rem 1.5rem;
            background: #3b82f6;
            color: white;
            border: none;
            border-radius: 4px;
            font-weight: 600;
            font-size: 0.875rem;
            cursor: pointer;
            transition: all 0.2s ease;
            white-space: nowrap;
            flex-shrink: 0;
        }

        .send-btn:hover:not(:disabled) {
            background: #2563eb;
        }

        .send-btn:disabled {
            opacity: 0.5;
            cursor: not-allowed;
        }

        .tabs {
            display: flex;
            padding: 0 1.5rem;
            gap: 0.5rem;
            background: #0d0d0d;
            border-bottom: 1px solid #262626;
            flex-shrink: 0;
        }

        /* Main Tabs (Request/Response) */
        .main-tabs {
            display: flex;
            gap: 0.8rem;
            margin-bottom: 1rem;
            border-bottom: 2px solid #262626;
            padding-bottom: 0;
        }

        .main-tab {
            padding: 0.6rem 0.8rem;
            color: #71717a;
            font-size: 0.9rem;
            font-weight: 600;
            cursor: pointer;
            border-bottom: 3px solid transparent;
            transition: all 0.2s ease;
        }

        .main-tab:hover {
            color: #e4e4e7;
        }

        .main-tab.active {
            color: #3b82f6;
            border-bottom-color: #3b82f6;
        }

        .main-view {
            display: none;
        }

        .main-view.active {
            display: block;
        }

        .tab {
            padding: 0.75rem 1rem;
            color: #71717a;
            font-size: 0.875rem;
            font-weight: 500;
            cursor: pointer;
            border-bottom: 2px solid transparent;
            transition: all 0.2s ease;
        }

        .tab:hover {
            color: #e4e4e7;
        }

        .tab.active {
            color: #3b82f6;
            border-bottom-color: #3b82f6;
        }

        .input-area {
            padding: 1.2rem;
            overflow: auto;
            display: none;
        }

        .input-area.active {
            display: flex;
            flex-direction: column;
        }

        .code-editor {
            width: 100%;
            padding: 1rem;
            background: #0d0d0d;
            border: 1px solid #262626;
            border-radius: 4px;
            color: #e4e4e7;
            font-family: 'Monaco', 'Courier New', monospace;
            font-size: 0.85rem;
            resize: none;
            line-height: 1.5;
            min-height: 200px;
        }

        .code-editor:focus {
            outline: none;
            border-color: #3b82f6;
            box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.1);
        }

        .response-section {
            background: #1a1a1a;
            border: 1px solid #262626;
            border-radius: 8px;
            overflow: hidden;
        }

        .response-header {
            padding: 1.2rem;
            border-bottom: 1px solid #262626;
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: #141414;
        }

        .response-title {
            font-weight: 600;
            color: #a1a1aa;
            font-size: 0.875rem;
        }

        .response-meta {
            display: flex;
            gap: 1rem;
            align-items: center;
        }

        .status-badge {
            padding: 0.25rem 0.75rem;
            border-radius: 4px;
            font-size: 0.75rem;
            font-weight: 600;
            border: 1px solid;
            display: none;
        }

        .status-badge.success {
            background: rgba(34, 197, 94, 0.1);
            color: #22c55e;
            border-color: rgba(34, 197, 94, 0.2);
        }

        .status-badge.error {
            background: rgba(239, 68, 68, 0.1);
            color: #ef4444;
            border-color: rgba(239, 68, 68, 0.2);
        }

        .status-badge.warning {
            background: rgba(245, 158, 11, 0.1);
            color: #f59e0b;
            border-color: rgba(245, 158, 11, 0.2);
        }

        .response-time {
            font-size: 0.75rem;
            color: #71717a;
        }

        .response-body {
            padding: 1.2rem;
            background: #0d0d0d;
            overflow-y: auto;
            font-family: 'Monaco', 'Courier New', monospace;
            font-size: 0.85rem;
            line-height: 1.5;
            color: #93c5fd;
            min-height: 250px;
        }

        .response-body::-webkit-scrollbar {
            width: 8px;
        }

        .response-body::-webkit-scrollbar-track {
            background: #0d0d0d;
        }

        .response-body::-webkit-scrollbar-thumb {
            background: #262626;
            border-radius: 4px;
        }

        .response-body::-webkit-scrollbar-thumb:hover {
            background: #3b82f6;
        }

        .empty-state {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100%;
            color: #71717a;
            text-align: center;
            gap: 1rem;
        }

        .empty-icon {
            font-size: 2.5rem;
            opacity: 0.5;
        }

        /* Right Sidebar */
        .right-sidebar {
            display: flex;
            flex-direction: column;
            gap: 1rem;
        }

        .collapsible {
            background: #1a1a1a;
            border: 1px solid #262626;
            border-radius: 8px;
            overflow: hidden;
        }

        .collapsible-header {
            padding: 0.8rem 1.2rem;
            cursor: pointer;
            display: flex;
            justify-content: space-between;
            align-items: center;
            transition: all 0.2s ease;
            user-select: none;
            background: #141414;
        }

        .collapsible-header:hover {
            background: #262626;
        }

        .collapsible-title {
            font-weight: 600;
            color: #e4e4e7;
            font-size: 0.95rem;
        }

        .collapsible-icon {
            color: #71717a;
            transition: transform 0.3s ease;
        }

        .collapsible-icon.open {
            transform: rotate(180deg);
        }

        .collapsible-content {
            max-height: 0;
            overflow: hidden;
            transition: max-height 0.3s ease-out;
        }

        .collapsible-content.open {
            max-height: 2000px;
            transition: max-height 0.5s ease-in;
        }

        .collapsible-body {
            padding: 1.5rem;
            color: #a1a1aa;
            font-size: 0.875rem;
            line-height: 1.8;
        }

        .collapsible-body h4 {
            color: #3b82f6;
            margin: 1rem 0 0.5rem 0;
            font-size: 0.9rem;
        }

        .collapsible-body h4:first-child {
            margin-top: 0;
        }

        .collapsible-body p {
            margin-bottom: 0.75rem;
        }

        .collapsible-body ul {
            list-style: none;
            padding-left: 0;
            margin: 0.75rem 0;
        }

        .collapsible-body li {
            padding-left: 1.5rem;
            position: relative;
            margin-bottom: 0.4rem;
        }

        .collapsible-body li:before {
            content: "→";
            position: absolute;
            left: 0;
            color: #3b82f6;
        }

        code {
            background: #0d0d0d;
            color: #60a5fa;
            padding: 0.2rem 0.4rem;
            border-radius: 3px;
            font-family: 'Monaco', 'Courier New', monospace;
            font-size: 0.8em;
            border: 1px solid #262626;
        }

        /* Help Modal */
        .help-btn {
            width: 40px;
            height: 40px;
            border-radius: 6px;
            border: 2px solid #3b82f6;
            background: #0d0d0d;
            color: #3b82f6;
            font-size: 1.2rem;
            cursor: pointer;
            transition: all 0.2s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
        }

        .help-btn:hover {
            background: #3b82f6;
            color: #0d0d0d;
        }

        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.7);
            z-index: 1000;
            align-items: center;
            justify-content: center;
        }

        .modal.active {
            display: flex;
        }

        .modal-content {
            background: #1a1a1a;
            border: 1px solid #262626;
            border-radius: 12px;
            width: 90%;
            max-width: 700px;
            max-height: 85vh;
            display: flex;
            flex-direction: column;
            overflow: hidden;
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.5);
            position: relative;
        }

        .modal-header {
            display: flex;
            justify-content: flex-start;
            align-items: center;
            padding: 1.5rem;
            border-bottom: 1px solid #262626;
            background: #141414;
            flex-shrink: 0;
        }

        .modal-title {
            font-size: 1.3rem;
            font-weight: 700;
            color: #fafafa;
        }

        .modal-close {
            width: 40px;
            height: 40px;
            border-radius: 6px;
            border: 2px solid #3b82f6;
            background: #0d0d0d;
            color: #3b82f6;
            font-size: 1.2rem;
            cursor: pointer;
            transition: all 0.2s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            padding: 0;
            flex-shrink: 0;
            position: absolute;
            top: 1.5rem;
            right: 1.5rem;
        }

        .modal-close:hover {
            background: #3b82f6;
            color: #0d0d0d;
        }

        .modal-body {
            overflow-y: auto;
            padding: 1.5rem;
            flex: 1;
        }

        .modal-body .section-title {
            display: none;
        }

        .modal-body::-webkit-scrollbar {
            width: 8px;
        }

        .modal-body::-webkit-scrollbar-track {
            background: #0d0d0d;
        }

        .modal-body::-webkit-scrollbar-thumb {
            background: #262626;
            border-radius: 4px;
        }

        .modal-body::-webkit-scrollbar-thumb:hover {
            background: #3b82f6;
        }

        /* Responsive */
        @media (max-width: 1400px) {
            .container {
                grid-template-columns: 1fr;
                gap: 1rem;
                padding: 1rem;
            }

            .sidebar {
                flex-direction: row;
                gap: 1rem;
            }

            .card {
                flex: 1;
            }

            .right-sidebar {
                flex-direction: row;
            }
        }

        /* Navigation Nodes */
        .section-nav {
            background: #1a1a1a;
            border-bottom: 1px solid #262626;
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
            background: rgba(0, 217, 255, 0.15);
            border-color: rgba(0, 217, 255, 0.8);
            color: #00d9ff;
            box-shadow: 0 0 15px rgba(0, 217, 255, 0.3);
        }

        .nav-node.unlocked:hover {
            background: rgba(0, 217, 255, 0.25);
            transform: scale(1.1);
        }

        .nav-node.visited {
            background: rgba(76, 175, 80, 0.2);
            border-color: rgba(102, 187, 106, 0.8);
            color: #4caf50;
            box-shadow: 0 0 15px rgba(76, 175, 80, 0.4);
        }

        .nav-node.current {
            background: #3b82f6;
            border-color: #3b82f6;
            color: #fff;
            box-shadow: 0 0 20px rgba(59, 130, 246, 0.6);
            transform: scale(1.15);
        }

        .nav-connector {
            width: 20px;
            height: 2px;
            background: #262626;
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

            .header {
                padding: 1rem;
            }

            .request-controls {
                flex-direction: column;
            }

            .url-input-group {
                width: 100%;
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

    <!-- Header -->
    <div class="header">
        <div class="header-left">
            <a href="/digitalmatchmaking/home/" style="display: inline-flex; align-items: center; gap: 0.5rem; text-decoration: none; color: inherit; transition: all 0.2s ease;">
                <span style="font-size: 1rem;">←</span>
                <span style="font-size: 0.85rem; color: #71717a; white-space: nowrap;">Back</span>
            </a>
            <div style="display: inline-flex; align-items: center; gap: 0.75rem; margin-left: 1.5rem;">
                <div class="header-icon">🔐</div>
                <div class="header-title">Account Port</div>
            </div>
        </div>
        <div style="display: flex; align-items: center; gap: 1rem;">
            <button class="help-btn" onclick="openHelpModal()" title="Help Documentation">?</button>
            <div class="auth-indicator">
                <div class="status-light" id="statusLight"></div>
                <span id="authStatus">Checking...</span>
            </div>
        </div>
    </div>

    <!-- Help Modal -->
    <div class="modal" id="helpModal" onclick="if(event.target === this) closeHelpModal()">
        <div class="modal-content">
            <div class="modal-header">
                <button class="modal-close" onclick="closeHelpModal()">✕</button>
            </div>
            <div class="modal-body" id="modalDocumentation">
                <!-- Documentation will be populated here -->
            </div>
        </div>
    </div>

    <!-- Main Container -->
    <div class="container">
        <!-- Request/Response Section -->
        <div class="section">
           
            
            <!-- Main Tabs -->
            <div class="main-tabs">
                <div class="main-tab active" onclick="switchMainTab('request', this)">📤 Request</div>
                <div class="main-tab" onclick="switchMainTab('response', this)">📥 Response</div>
            </div>

            <!-- Request View -->
            <div id="requestView" class="main-view active">
                <div style="margin-bottom: 1.5rem; display: flex; gap: 1rem; flex-wrap: wrap;">
                    <div class="action-btn" onclick="loadExample('setup')">
                        <span class="action-icon">🔧</span>
                        <span>Setup Account</span>
                    </div>
                    <div class="action-btn" onclick="loadExample('get')">
                        <span class="action-icon">👤</span>
                        <span>Get User Info</span>
                    </div>
                </div>

                <div class="request-controls">
                    <select id="method" class="method-select">
                        <option value="GET">GET</option>
                        <option value="POST">POST</option>
                        <option value="PUT">PUT</option>
                        <option value="DELETE">DELETE</option>
                    </select>
                    <div class="url-input-group">
                        <input type="text" id="url" class="url-input" placeholder="Enter API endpoint URL" />
                        <button id="sendBtn" class="send-btn" onclick="sendRequest()">Send</button>
                    </div>
                </div>

                <div class="tabs">
                    <div class="tab active" onclick="switchTab('body')">Body</div>
                    <div class="tab" onclick="switchTab('headers')">Headers</div>
                </div>

                <div class="input-area active" id="bodyArea">
                    <textarea id="requestBody" class="code-editor" placeholder='{"key": "value"}'>{}</textarea>
                </div>

                <div class="input-area" id="headersArea">
                    <div style="color: #71717a; padding: 1rem;">Headers are automatically set for authentication</div>
                </div>
            </div>

            <!-- Response View -->
            <div id="responseView" class="main-view">
                <div class="response-header">
                    <div class="response-title">Status & Timing</div>
                    <div class="response-meta">
                        <div id="statusBadge" class="status-badge"></div>
                        <div id="responseTime" class="response-time"></div>
                    </div>
                </div>
                <div class="response-body" id="responseBody">
                    <div class="empty-state">
                        <div class="empty-icon">📭</div>
                        <div>Send a request to see the response</div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Help Documentation -->
        <div id="documentationContent" style="display: none;">
            <div class="section help-sidebar">
                <div class="section-title">Documentation</div>
                <!-- Getting Started -->
                <div class="collapsible">
                    <div class="collapsible-header" onclick="toggleCollapsible(this)">
                        <div class="collapsible-title">📖 Getting Started</div>
                        <div class="collapsible-icon">▼</div>
                    </div>
                    <div class="collapsible-content open">
                        <div class="collapsible-body">
                            <h4>Step 1: Create Account</h4>
                            <p>Click "Create Account" to initialize your profile. Expect status 201.</p>

                            <h4>Step 2: Add Data</h4>
                            <p>Use "Add Profile Data" to add information like hobbies, interests, skills, etc.</p>

                            <h4>Step 3: View Profile</h4>
                            <p>Click "View Profile" to see all saved data.</p>

                            <h4>Status Codes</h4>
                            <ul>
                                <li><code>200</code> - Success</li>
                                <li><code>201</code> - Created</li>
                                <li><code>404</code> - Not Found</li>
                                <li><code>409</code> - Conflict</li>
                            </ul>
                        </div>
                    </div>
                </div>

                <!-- API Overview -->
                <div class="collapsible">
                    <div class="collapsible-header" onclick="toggleCollapsible(this)">
                        <div class="collapsible-title">🎯 What is This?</div>
                        <div class="collapsible-icon">▼</div>
                    </div>
                    <div class="collapsible-content">
                        <div class="collapsible-body">
                            <p>Account Port is an API testing interface for the Matchmaking service. It allows you to interact with backend endpoints in real-time.</p>

                            <h4>Key Features</h4>
                            <ul>
                                <li>Test API endpoints</li>
                                <li>Manage user profiles</li>
                                <li>Save profile data</li>
                                <li>View responses in real-time</li>
                            </ul>
                        </div>
                    </div>
                </div>

                <!-- How It Works -->
                <div class="collapsible">
                    <div class="collapsible-header" onclick="toggleCollapsible(this)">
                        <div class="collapsible-title">💡 How It Works</div>
                        <div class="collapsible-icon">▼</div>
                    </div>
                    <div class="collapsible-content">
                        <div class="collapsible-body">
                            <p>This tool communicates directly with the backend API using HTTP requests.</p>

                            <h4>The Process</h4>
                            <ul>
                                <li>Select HTTP method (GET, POST, PUT, DELETE)</li>
                                <li>Enter the API endpoint URL</li>
                                <li>Add request body (for POST/PUT)</li>
                                <li>Click Send to execute request</li>
                                <li>View response with status code</li>
                            </ul>

                            <h4>Authentication</h4>
                            <p>Your session is automatically authenticated. You must be logged in to use this tool.</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script type="module">
        import { pythonURI, fetchOptions } from '/digitalmatchmaking/assets/js/api/config.js';

        let isAuthenticated = false;
        let hasAccount = false;

        // DOM Elements
        const statusLight = document.getElementById('statusLight');
        const authStatus = document.getElementById('authStatus');
        const accountIcon = document.getElementById('accountIcon');
        const accountStatus = document.getElementById('accountStatus');
        const methodSelect = document.getElementById('method');
        const urlInput = document.getElementById('url');
        const requestBody = document.getElementById('requestBody');
        const sendBtn = document.getElementById('sendBtn');
        const responseBody = document.getElementById('responseBody');
        const statusBadge = document.getElementById('statusBadge');
        const responseTime = document.getElementById('responseTime');

        urlInput.value = `${pythonURI}/api/match/data`;

        // Check Authentication
        async function checkAuth() {
            try {
                const response = await fetch(`${pythonURI}/api/id`, {
                    ...fetchOptions,
                    credentials: 'include'
                });

                if (response.ok) {
                    isAuthenticated = true;
                    statusLight.classList.add('active');
                    await checkAccountStatus();
                    return;
                }
            } catch (error) {
                console.error('Auth check failed:', error);
            }

            isAuthenticated = false;
            hasAccount = false;
            statusLight.classList.remove('active');
            authStatus.textContent = 'Not Logged In';
            updateNavigation();
        }

        // Check Account Status
        async function checkAccountStatus() {
            if (!isAuthenticated) return;

            try {
                const response = await fetch(`${pythonURI}/api/match/data`, {
                    method: 'GET',
                    credentials: 'include',
                    headers: {
                        'Content-Type': 'application/json',
                        'X-Origin': 'client'
                    }
                });

                if (response.ok) {
                    hasAccount = true;
                    authStatus.textContent = '✅ Account Active';
                } else {
                    hasAccount = false;
                    authStatus.textContent = '❌ No Account';
                }
                updateNavigation();
            } catch (error) {
                console.error('Account check failed:', error);
                hasAccount = false;
                authStatus.textContent = '❌ No Account';
                updateNavigation();
            }
        }

        // Tab Switching
        window.switchTab = function(tab) {
            document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
            document.querySelectorAll('.input-area').forEach(a => a.classList.remove('active'));
            event.target.classList.add('active');
            document.getElementById(`${tab}Area`).classList.add('active');
        };

        // Main Tab Switching (Request/Response)
        window.switchMainTab = function(view, tabElement) {
            document.querySelectorAll('.main-tab').forEach(t => t.classList.remove('active'));
            document.querySelectorAll('.main-view').forEach(v => v.classList.remove('active'));
            tabElement.classList.add('active');
            document.getElementById(`${view}View`).classList.add('active');
        };

        // Load Example
        window.loadExample = function(type) {
            if (!isAuthenticated) {
                alert('Please log in to use the API tester');
                return;
            }

            const examples = {
                setup: {
                    method: 'POST',
                    url: `${pythonURI}/api/match/setup`,
                    body: '{}'
                },
                add: {
                    method: 'POST',
                    url: `${pythonURI}/api/match/add`,
                    body: JSON.stringify({
                        index: 'favorite_hobby',
                        data: 'Reading and coding'
                    }, null, 2)
                },
                get: {
                    method: 'GET',
                    url: `${pythonURI}/api/match/data`,
                    body: '{}'
                }
            };

            const ex = examples[type];
            methodSelect.value = ex.method;
            urlInput.value = ex.url;
            requestBody.value = ex.body;
        };

        // Format JSON
        function formatJSON(obj) {
            const json = JSON.stringify(obj, null, 2);
            return json
                .replace(/"([^"]+)":/g, '<span style="color: #60a5fa">"$1"</span>:')
                .replace(/: "([^"]*)"/g, ': <span style="color: #34d399">"$1"</span>')
                .replace(/: (\d+)/g, ': <span style="color: #fbbf24">$1</span>')
                .replace(/: (true|false)/g, ': <span style="color: #c084fc">$1</span>')
                .replace(/: null/g, ': <span style="color: #9ca3af">null</span>');
        }

        // Send Request
        window.sendRequest = async function() {
            if (!isAuthenticated) {
                alert('Please log in to use the API tester');
                return;
            }

            const method = methodSelect.value;
            const url = urlInput.value;
            const body = requestBody.value;

            sendBtn.disabled = true;
            sendBtn.textContent = 'Sending...';
            statusBadge.style.display = 'none';
            responseTime.textContent = '';

            try {
                const options = {
                    method: method,
                    credentials: 'include',
                    headers: {
                        'Content-Type': 'application/json',
                        'X-Origin': 'client'
                    }
                };

                if (method !== 'GET') {
                    try {
                        JSON.parse(body);
                        options.body = body;
                    } catch (e) {
                        responseBody.innerHTML = '<div style="color: #ef4444;">Invalid JSON in request body</div>';
                        sendBtn.disabled = false;
                        sendBtn.textContent = 'Send';
                        return;
                    }
                }

                const startTime = Date.now();
                const response = await fetch(url, options);
                const duration = Date.now() - startTime;

                statusBadge.textContent = `${response.status} ${response.statusText}`;
                statusBadge.style.display = 'block';

                if (response.status >= 200 && response.status < 300) {
                    statusBadge.className = 'status-badge success';
                } else if (response.status >= 400 && response.status < 500) {
                    statusBadge.className = 'status-badge error';
                } else {
                    statusBadge.className = 'status-badge warning';
                }

                responseTime.textContent = `${duration}ms`;

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

                responseBody.innerHTML = `<pre>${formatJSON(responseObj)}</pre>`;
                await checkAccountStatus();

                // Auto-switch to Response view
                const responseTab = document.querySelector('.main-tab:nth-child(2)');
                switchMainTab('response', responseTab);

            } catch (error) {
                responseBody.innerHTML = `<div style="color: #ef4444;">Error: ${error.message}</div>`;
                statusBadge.style.display = 'none';
                
                // Auto-switch to Response view to show error
                const responseTab = document.querySelector('.main-tab:nth-child(2)');
                switchMainTab('response', responseTab);
            }

            sendBtn.disabled = false;
            sendBtn.textContent = 'Send';
        };

        // Toggle Collapsible
        window.toggleCollapsible = function(header) {
            const content = header.nextElementSibling;
            const icon = header.querySelector('.collapsible-icon');

            content.classList.toggle('open');
            icon.classList.toggle('open');
        };

        // Help Modal Functions
        window.openHelpModal = function() {
            const modal = document.getElementById('helpModal');
            const docContent = document.getElementById('documentationContent');
            const modalBody = document.getElementById('modalDocumentation');
            
            // Clone the documentation into the modal
            modalBody.innerHTML = docContent.innerHTML;
            modal.classList.add('active');
            document.body.style.overflow = 'hidden';
        };

        window.closeHelpModal = function() {
            const modal = document.getElementById('helpModal');
            modal.classList.remove('active');
            document.body.style.overflow = 'auto';
        };

        // Close modal when pressing Escape
        document.addEventListener('keydown', function(e) {
            if (e.key === 'Escape') {
                closeHelpModal();
            }
        });

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
            // Pages 2+ require account to be created
            if (!hasAccount) return false;
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

        // Initialize
        checkAuth();
    </script>
</body>
</html>
