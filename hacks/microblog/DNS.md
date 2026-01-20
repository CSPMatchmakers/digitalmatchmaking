---
layout: post
title: "DNS"
description: "Submodule 4 of Hints Mini-Quest"
permalink: /dns/
parent: "AI Usage"
team: "FlaskLovers"
submodule: 2
categories: [CSP, Submodule, Microblogging]
tags: [microblogging, submodule, unzippers]
author: "Adhav Selvan"
date: 2025-12-01
breadcrumb: true
backend_enabled: true
backend_api: "/api"
---

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AP CSP: REST API & Matchmaking</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://unpkg.com/lucide@latest"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700&display=swap');
        body { font-family: 'Inter', sans-serif; }
        .server-box { transition: all 0.5s ease; }
        
        @keyframes slide-in {
            from { transform: translateX(-20px); opacity: 0; }
            to { transform: translateX(0); opacity: 1; }
        }
        .slide-in { animation: slide-in 0.3s ease; }
    </style>
    
    <!-- Import config.js FIRST, before main game script -->
    <script type="module">
        try {
            const baseurl = "{{ site.baseurl }}";
            console.log('Attempting to import config.js from:', baseurl + '/assets/js/api/config.js');
            
            const mod = await import(baseurl + '/assets/js/api/config.js');
            
            // Set on window object so inline scripts can access it
            window._apiImportedConfig = {
                pythonURI: mod.pythonURI,
                fetchOptions: mod.fetchOptions
            };
            window.pythonURI = mod.pythonURI;  // Also set here for easy access
            
            console.log('✓ matchmakingLesson: config imported successfully');
            console.log('✓ pythonURI from config:', mod.pythonURI);
            console.log('✓ window.pythonURI set to:', window.pythonURI);
        } catch (err) {
            console.warn('✗ matchmakingLesson: could not import config.js', err);
            console.warn('Will use hostname-based fallback');
            
            // Set fallback directly
            if (location.hostname === "localhost" || location.hostname === "127.0.0.1") {
                window._apiImportedConfig = {
                    pythonURI: "http://localhost:8401"
                };
                window.pythonURI = "http://localhost:8401";
                console.log('✓ Set fallback pythonURI: http://localhost:8401');
            }
        }
    </script>
</head>
<body class="bg-slate-900 text-slate-100 min-h-screen flex flex-col">

    <!-- Header -->
    <header class="bg-slate-800 border-b border-slate-700 p-4 shadow-lg sticky top-0 z-50">
        <div class="max-w-5xl mx-auto flex justify-between items-center">
            <h1 class="text-2xl font-bold text-blue-400 flex items-center gap-2">
                <i data-lucide="server" class="w-6 h-6"></i>
                AP CSP: REST API Request Matching
            </h1>
            <div class="text-sm text-slate-400">Topic: Flask Endpoints & Server Integration</div>
        </div>
    </header>

    <main class="flex-grow p-6 max-w-5xl mx-auto w-full space-y-12">

        <!-- LECTURE INTRO -->
        <article class="prose prose-invert max-w-none">
            <h2 class="text-3xl font-light text-white border-b border-slate-700 pb-2">Understanding API Endpoint Matching</h2>
            <p class="text-lg text-slate-300 leading-relaxed">
                A REST API is a system where the frontend (user-facing interface) communicates with the backend (server) through standardized endpoints. Each endpoint is like a function you can call over the internet. When you send an HTTP request to an endpoint, the server must match that request to the correct handler, validate the data, and execute the appropriate logic.
            </p>
            <p class="text-lg text-slate-300 leading-relaxed">
                Your Flask API manages user profile data by matching requests to endpoints. Each endpoint has a specific purpose, validates input, stores or retrieves data, and returns a response. This lesson teaches you to match HTTP requests with their intended endpoints and understand the data flow from frontend to backend.
            </p>
            <div class="grid md:grid-cols-2 gap-6 my-6">
                <div class="bg-slate-800 p-4 rounded border border-slate-700">
                    <h4 class="font-bold text-blue-400 mb-2">Frontend Request</h4>
                    <p class="text-sm text-slate-400">The browser sends an HTTP request (GET, POST, DELETE) with a URL path, optional headers (like JWT token), and optional body data (JSON).</p>
                </div>
                <div class="bg-slate-800 p-4 rounded border border-slate-700">
                    <h4 class="font-bold text-purple-400 mb-2">Backend Response</h4>
                    <p class="text-sm text-slate-400">The Flask server matches the request to an endpoint, executes the handler logic, reads/writes data, and returns a JSON response with a status code (200, 201, 400, 404, etc.).</p>
                </div>
            </div>
        </article>

        <!-- LECTURE BRIDGE 1 -->
        <article class="prose prose-invert max-w-none">
            <h2 class="text-3xl font-light text-white border-b border-slate-700 pb-2">Flask API Architecture: Blueprint Organization</h2>
            <div class="bg-blue-900/20 border-l-4 border-blue-500 p-4 my-4">
                <p class="font-bold text-blue-200 m-0">Key Principle: Request Routing</p>
                <p class="text-blue-100 m-0 text-sm">Flask receives HTTP requests and matches them to endpoints using URL patterns, HTTP methods, and request data. Each endpoint handler is a procedure that validates input, processes data, and returns output.</p>
            </div>
            <p class="text-lg text-slate-300 leading-relaxed">
                Your matchmaking API is organized as a Blueprint with the URL prefix <code>/api/match</code>. This groups all profile-related endpoints together. When a request arrives at the server, Flask checks:
            </p>
            <ul class="list-none pl-0 text-slate-300 space-y-4 my-6">
                <li class="flex items-start gap-3">
                    <span class="bg-blue-900/50 text-blue-200 px-3 py-1 rounded text-sm font-mono border border-blue-500 shrink-0">URL Match</span>
                    <span>Does the request URL match a registered endpoint? (e.g., <code>/api/match/data</code> matches the _DATA resource)</span>
                </li>
                <li class="flex items-start gap-3">
                    <span class="bg-blue-900/50 text-blue-200 px-3 py-1 rounded text-sm font-mono border border-blue-500 shrink-0">Method Match</span>
                    <span>Is the HTTP method (GET, POST, DELETE) supported by this endpoint? (e.g., _DATA only handles GET, not POST)</span>
                </li>
                <li class="flex items-start gap-3">
                    <span class="bg-blue-900/50 text-blue-200 px-3 py-1 rounded text-sm font-mono border border-blue-500 shrink-0">Auth Match</span>
                    <span>Does the request include valid JWT authentication? The <code>@token_required()</code> decorator validates this before the handler executes.</span>
                </li>
                <li class="flex items-start gap-3">
                    <span class="bg-blue-900/50 text-blue-200 px-3 py-1 rounded text-sm font-mono border border-blue-500 shrink-0">Data Match</span>
                    <span>Are required fields present in the request body? (e.g., _ADD expects both "index" and "data" fields)</span>
                </li>
            </ul>
        </article>

        <!-- SECTION 1: ENDPOINT DETAILS -->
        <section id="endpoint-details" class="bg-slate-800 rounded-xl p-6 shadow-xl border border-slate-700">
            <h2 class="text-xl font-semibold mb-4 text-emerald-400 flex items-center gap-2">
                <i data-lucide="link-2" class="w-5 h-5"></i>
                Part 1: Understanding Your Endpoints
            </h2>
            <p class="mb-6 text-slate-300">
                Below are your actual Flask endpoints. Each one handles a specific type of request. Hover over each endpoint to see its matching logic, required inputs, and expected outputs.
            </p>

            <div class="space-y-4">
                <div class="group bg-slate-900 p-4 rounded-lg border border-slate-700 hover:border-blue-500 transition-colors cursor-help">
                    <div class="flex items-center justify-between">
                        <div>
                            <h3 class="font-bold text-blue-400">GET /api/match/data</h3>
                            <p class="text-sm text-slate-400">Retrieve current user's profile</p>
                        </div>
                        <i data-lucide="chevron-down" class="w-5 h-5 text-slate-500 group-hover:text-blue-400 transition-colors"></i>
                    </div>
                    <div class="hidden group-hover:block mt-4 space-y-2 text-sm text-slate-300 bg-slate-800/50 p-3 rounded">
                        <div><span class="text-blue-300 font-bold">Input:</span> JWT token in header</div>
                        <div><span class="text-blue-300 font-bold">Matching:</span> Validates token, extracts UID, searches profile_setups for matching user</div>
                        <div><span class="text-blue-300 font-bold">Output:</span> {"message": "...", "setup": {...}} with status 200 or 404</div>
                    </div>
                </div>

                <div class="group bg-slate-900 p-4 rounded-lg border border-slate-700 hover:border-green-500 transition-colors cursor-help">
                    <div class="flex items-center justify-between">
                        <div>
                            <h3 class="font-bold text-green-400">POST /api/match/setup</h3>
                            <p class="text-sm text-slate-400">Initialize new profile setup</p>
                        </div>
                        <i data-lucide="chevron-down" class="w-5 h-5 text-slate-500 group-hover:text-green-400 transition-colors"></i>
                    </div>
                    <div class="hidden group-hover:block mt-4 space-y-2 text-sm text-slate-300 bg-slate-800/50 p-3 rounded">
                        <div><span class="text-green-300 font-bold">Input:</span> JWT token in header</div>
                        <div><span class="text-green-300 font-bold">Matching:</span> Validates token, checks if profile_setup_exists(uid). Returns 409 if exists, creates new record and returns 201 if doesn't.</div>
                        <div><span class="text-green-300 font-bold">Output:</span> {"message": "...", "setup": {...}} with status 201 or 409</div>
                    </div>
                </div>

                <div class="group bg-slate-900 p-4 rounded-lg border border-slate-700 hover:border-purple-500 transition-colors cursor-help">
                    <div class="flex items-center justify-between">
                        <div>
                            <h3 class="font-bold text-purple-400">POST /api/match/add</h3>
                            <p class="text-sm text-slate-400">Add indexed data to profile</p>
                        </div>
                        <i data-lucide="chevron-down" class="w-5 h-5 text-slate-500 group-hover:text-purple-400 transition-colors"></i>
                    </div>
                    <div class="hidden group-hover:block mt-4 space-y-2 text-sm text-slate-300 bg-slate-800/50 p-3 rounded">
                        <div><span class="text-purple-300 font-bold">Input:</span> JWT + JSON body: {"index": "field_name", "data": value}</div>
                        <div><span class="text-purple-300 font-bold">Matching:</span> Validates token and body fields. Searches user in setups, creates profile if missing, adds/updates user_setup['data'][index] = data</div>
                        <div><span class="text-purple-300 font-bold">Output:</span> {"message": "...", "index": "...", "data": ...} with status 201</div>
                    </div>
                </div>

                <div class="group bg-slate-900 p-4 rounded-lg border border-slate-700 hover:border-pink-500 transition-colors cursor-help">
                    <div class="flex items-center justify-between">
                        <div>
                            <h3 class="font-bold text-pink-400">POST /api/match/save-profile-json</h3>
                            <p class="text-sm text-slate-400">Save quiz/game profile data</p>
                        </div>
                        <i data-lucide="chevron-down" class="w-5 h-5 text-slate-500 group-hover:text-pink-400 transition-colors"></i>
                    </div>
                    <div class="hidden group-hover:block mt-4 space-y-2 text-sm text-slate-300 bg-slate-800/50 p-3 rounded">
                        <div><span class="text-pink-300 font-bold">Input:</span> JWT + JSON body: {"profile_data": [{"question": "q", "response": "r"}, ...]}</div>
                        <div><span class="text-pink-300 font-bold">Matching:</span> Validates token and profile_data array. Creates profile if missing. Merges each question→response into user_setup['data']. Persists to JSON file.</div>
                        <div><span class="text-pink-300 font-bold">Output:</span> {"message": "...", "setup": {...}} with status 201</div>
                    </div>
                </div>
            </div>

            <div class="mt-6 p-4 bg-slate-700/50 rounded border-l-4 border-blue-500">
                <h3 class="font-bold text-blue-400 text-sm uppercase">Component A Compliance</h3>
                <p class="text-sm text-slate-300 mt-1">
                    These endpoints demonstrate the requirements: <strong>Input</strong> from user (JWT + JSON body), <strong>List data structure</strong> (profile_data array, user setups collection), <strong>Procedures</strong> (each endpoint function with parameters and return values), <strong>Sequencing & Selection</strong> (conditional matching logic), <strong>Iteration</strong> (searching through setups array), and <strong>Output</strong> (JSON responses with visual status in the game).
                </p>
            </div>
        </section>

        <!-- SECTION 2: MATCHING GAME -->
        <section id="matching-game" class="bg-slate-800 rounded-xl p-6 shadow-xl border border-slate-700">
            <h2 class="text-xl font-semibold mb-2 text-pink-400 flex items-center gap-2">
                <i data-lucide="gamepad-2" class="w-5 h-5"></i>
                Part 2: The Endpoint Matching Game
            </h2>
            <p class="mb-6 text-slate-300">
                You are a Flask Router. Match incoming HTTP requests (left) with the correct endpoints (right). Consider the HTTP method, required data, and endpoint purpose. Click pairs to match them. You have 3 mistakes before game over!
            </p>

            <!-- Game Stats -->
            <div class="grid grid-cols-3 gap-4 mb-6">
                <div class="bg-slate-900 p-3 rounded border border-slate-600 text-center">
                    <p class="text-xs text-slate-400">Score</p>
                    <p class="text-2xl font-bold text-green-400" id="score">0</p>
                </div>
                <div class="bg-slate-900 p-3 rounded border border-slate-600 text-center">
                    <p class="text-xs text-slate-400">Mistakes Remaining</p>
                    <p class="text-2xl font-bold text-red-400" id="mistakes">3</p>
                </div>
                <div class="bg-slate-900 p-3 rounded border border-slate-600 text-center">
                    <p class="text-xs text-slate-400">Matches Found</p>
                    <p class="text-2xl font-bold text-blue-400" id="matches">0/5</p>
                </div>
            </div>

            <!-- Game Board -->
            <div class="bg-slate-900 p-8 rounded-lg border border-slate-700">
                <div id="game-board" class="grid grid-cols-2 gap-4 md:gap-6">
                    <!-- Cards will be generated by JavaScript -->
                </div>
            </div>

            <!-- Action Buttons -->
            <div class="flex gap-2 mt-6">
                <button onclick="initializeGame()" class="bg-blue-600 hover:bg-blue-500 text-white px-6 py-2 rounded font-bold transition-colors flex items-center gap-2">
                    <i data-lucide="rotate-cw" class="w-4 h-4"></i> New Game
                </button>
                <button onclick="showHint()" id="hint-btn" class="bg-slate-700 hover:bg-slate-600 text-white px-6 py-2 rounded font-bold transition-colors flex items-center gap-2">
                    <i data-lucide="lightbulb" class="w-4 h-4"></i> Hint
                </button>
            </div>

            <!-- Game Over Message -->
            <div id="game-over" class="hidden mt-6 p-4 rounded-lg bg-green-900/30 border border-green-500 slide-in">
                <h3 class="font-bold text-green-400 mb-2 flex items-center gap-2">
                    <i data-lucide="trophy" class="w-5 h-5"></i> Congratulations!
                </h3>
                <p class="text-green-200 text-sm">You successfully matched all requests to endpoints! You understand how Flask routes HTTP requests to the correct handlers and processes data.</p>
                <button onclick="saveProgress()" class="mt-4 bg-green-600 hover:bg-green-500 text-white px-6 py-2 rounded font-bold transition-colors flex items-center gap-2">
                    <i data-lucide="upload" class="w-4 h-4"></i> Save Progress to Server
                </button>
            </div>

            <!-- Loss Message -->
            <div id="game-lost" class="hidden mt-6 p-4 rounded-lg bg-red-900/30 border border-red-500 slide-in">
                <h3 class="font-bold text-red-400 mb-2 flex items-center gap-2">
                    <i data-lucide="x-circle" class="w-5 h-5"></i> Game Over
                </h3>
                <p class="text-red-200 text-sm">You made too many mistakes. Request routing requires precision! Try again to improve your understanding of Flask endpoints.</p>
            </div>

            <!-- Server Status -->
            <div id="server-status" class="mt-4 p-3 rounded-lg bg-slate-900 border border-slate-700 text-center text-sm">
                <span class="text-slate-400">Server Status: </span>
                <span id="status-text" class="text-yellow-400">Checking...</span>
            </div>
        </section>

        <!-- SECTION 3: DATA FLOW EXPLANATION -->
        <article class="prose prose-invert max-w-none">
            <h2 class="text-3xl font-light text-white border-b border-slate-700 pb-2">Understanding the Request-Response Cycle</h2>
            <p class="text-lg text-slate-300 leading-relaxed">
                When you play the matching game, you're simulating what happens every time a real user interacts with the API. Here's the complete data flow:
            </p>

            <div class="space-y-4 mt-6">
                <div class="bg-slate-800 p-4 rounded-lg">
                    <h3 class="text-blue-400 font-bold mb-2">Step 1: Frontend Sends Request</h3>
                    <p class="text-slate-400 text-sm">
                        The frontend (your browser/app) collects user input (quiz answers, game scores, profile data). It packages this data into a JSON body and sends an HTTP POST request to <code>/api/match/save-profile-json</code> with a JWT token in the Authorization header.
                    </p>
                </div>

                <div class="bg-slate-800 p-4 rounded-lg">
                    <h3 class="text-purple-400 font-bold mb-2">Step 2: Flask Matches Request to Endpoint</h3>
                    <p class="text-slate-400 text-sm">
                        Flask receives the request and checks: Is this URL registered? Does it match <code>/api/match/save-profile-json</code>? Is the method POST? The SaveProfileJSON resource's post() method is selected.
                    </p>
                </div>

                <div class="bg-slate-800 p-4 rounded-lg">
                    <h3 class="text-green-400 font-bold mb-2">Step 3: Endpoint Validates Input</h3>
                    <p class="text-slate-400 text-sm">
                        The @token_required() decorator runs first, validating the JWT and extracting the user's UID. Then the handler checks: Does the request body have profile_data? If not, return 400. If yes, proceed.
                    </p>
                </div>

                <div class="bg-slate-800 p-4 rounded-lg">
                    <h3 class="text-orange-400 font-bold mb-2">Step 4: Endpoint Processes Data</h3>
                    <p class="text-slate-400 text-sm">
                        The handler reads the JSON file containing all user profiles. It searches for the current user's setup using the UID. If not found, it creates a new one. It then iterates through the profile_data array and merges each question-response pair into the user's data dictionary.
                    </p>
                </div>

                <div class="bg-slate-800 p-4 rounded-lg">
                    <h3 class="text-cyan-400 font-bold mb-2">Step 5: Endpoint Persists Data & Responds</h3>
                    <p class="text-slate-400 text-sm">
                        The handler writes the updated profiles back to the JSON file using _write_profile_setups(). It returns a JSON response with status 201 Created, including the updated user setup. The frontend receives this response and updates the UI to show success.
                    </p>
                </div>
            </div>
        </article>

        <!-- SECTION 4: ADVANCED CONCEPTS -->
        <section class="bg-slate-800 rounded-xl p-6 shadow-xl border border-slate-700">
            <h2 class="text-xl font-semibold mb-4 text-cyan-400 flex items-center gap-2">
                <i data-lucide="brain" class="w-5 h-5"></i>
                Part 3: Advanced API Concepts
            </h2>
            
            <div class="space-y-4">
                <div class="bg-slate-900 p-4 rounded border border-slate-600">
                    <p class="font-semibold text-sm text-slate-200 mb-2">Status Codes & Semantic Meaning</p>
                    <p class="text-xs text-slate-400">
                        <strong>200 OK:</strong> Request succeeded, data retrieved. <strong>201 Created:</strong> New resource created. <strong>400 Bad Request:</strong> Client sent invalid data (missing required fields). <strong>404 Not Found:</strong> Resource doesn't exist. <strong>409 Conflict:</strong> Operation conflicts with existing state. <strong>500 Internal Server Error:</strong> Server crashed (caught by try/except).
                    </p>
                </div>

                <div class="bg-slate-900 p-4 rounded border border-slate-600">
                    <p class="font-semibold text-sm text-slate-200 mb-2">JWT Authentication & Authorization</p>
                    <p class="text-xs text-slate-400">
                        The @token_required() decorator validates the JWT token and extracts the current_user. This ensures: (1) Only authenticated users can access endpoints, (2) Each request is tied to a specific user UID, (3) Users can only access/modify their own data. Without JWT validation, any malicious actor could access or delete other users' profiles.
                    </p>
                </div>

                <div class="bg-slate-900 p-4 rounded border border-slate-600">
                    <p class="font-semibold text-sm text-slate-200 mb-2">Request Body Validation & Error Handling</p>
                    <p class="text-xs text-slate-400">
                        Before writing to the database, endpoints validate: Does the request body exist? Are required fields present? The _ADD endpoint checks body.get('index') and body.get('data'). If either is missing, it returns 400 immediately. This defensive programming prevents invalid data from corrupting the JSON file. Try/except blocks catch file I/O errors and return 500 with a message.
                    </p>
                </div>

                <div class="bg-slate-900 p-4 rounded border border-slate-600">
                    <p class="font-semibold text-sm text-slate-200 mb-2">Idempotency & State Checking</p>
                    <p class="text-xs text-slate-400">
                        The _SETUP endpoint checks if a profile already exists before creating one. Calling POST /api/match/setup twice should not create two profiles. This is idempotency—the system's state after N identical requests should equal the state after 1 request. Idempotent APIs are crucial for reliability when network failures cause duplicate requests.
                    </p>
                </div>

                <div class="bg-slate-900 p-4 rounded border border-slate-600">
                    <p class="font-semibold text-sm text-slate-200 mb-2">Statelessness & Scalability</p>
                    <p class="text-xs text-slate-400">
                        Each Flask request is stateless. The handler doesn't remember previous requests. It reads everything it needs (from JWT, request body, JSON file) and responds. This design enables horizontal scaling—run multiple Flask instances on different servers, and any instance can handle any request. The JSON file (or database) is the single source of truth.
                    </p>
                </div>
            </div>
        </section>

        <!-- SECTION 5: QUICK CHECK QUIZ -->
        <section class="bg-slate-800 rounded-xl p-6 shadow-xl border border-slate-700">
             <h2 class="text-xl font-semibold mb-4 text-purple-400 flex items-center gap-2">
                <i data-lucide="clipboard-check" class="w-5 h-5"></i>
                Part 4: Quick Check
            </h2>
            <div class="grid md:grid-cols-2 gap-4">
                <div class="bg-slate-900 p-4 rounded border border-slate-600">
                    <p class="font-semibold text-sm mb-3">1. What does @token_required() do?</p>
                    <button class="w-full text-left p-2 text-sm hover:bg-slate-800 rounded transition-colors border border-transparent hover:border-slate-500 mb-1" onclick="checkAnswer(this, false)">Encrypts the user's data before storing.</button>
                    <button class="w-full text-left p-2 text-sm hover:bg-slate-800 rounded transition-colors border border-transparent hover:border-slate-500 mb-1" onclick="checkAnswer(this, true)">Validates JWT and extracts current user before endpoint executes.</button>
                    <button class="w-full text-left p-2 text-sm hover:bg-slate-800 rounded transition-colors border border-transparent hover:border-slate-500" onclick="checkAnswer(this, false)">Automatically saves data to the JSON file.</button>
                </div>

                <div class="bg-slate-900 p-4 rounded border border-slate-600">
                    <p class="font-semibold text-sm mb-3">2. What status code means a new resource was created?</p>
                    <button class="w-full text-left p-2 text-sm hover:bg-slate-800 rounded transition-colors border border-transparent hover:border-slate-500 mb-1" onclick="checkAnswer(this, false)">200 OK</button>
                    <button class="w-full text-left p-2 text-sm hover:bg-slate-800 rounded transition-colors border border-transparent hover:border-slate-500 mb-1" onclick="checkAnswer(this, true)">201 Created</button>
                    <button class="w-full text-left p-2 text-sm hover:bg-slate-800 rounded transition-colors border border-transparent hover:border-slate-500" onclick="checkAnswer(this, false)">400 Bad Request</button>
                </div>

                <div class="bg-slate-900 p-4 rounded border border-slate-600">
                    <p class="font-semibold text-sm mb-3">3. What does _SETUP return if a profile already exists?</p>
                    <button class="w-full text-left p-2 text-sm hover:bg-slate-800 rounded transition-colors border border-transparent hover:border-slate-500 mb-1" onclick="checkAnswer(this, false)">200 OK with the existing profile</button>
                    <button class="w-full text-left p-2 text-sm hover:bg-slate-800 rounded transition-colors border border-transparent hover:border-slate-500 mb-1" onclick="checkAnswer(this, true)">409 Conflict (already created)</button>
                    <button class="w-full text-left p-2 text-sm hover:bg-slate-800 rounded transition-colors border border-transparent hover:border-slate-500" onclick="checkAnswer(this, false)">500 Internal Server Error</button>
                </div>

                <div class="bg-slate-900 p-4 rounded border border-slate-600">
                    <p class="font-semibold text-sm mb-3">4. Why validate request body data before writing to the database?</p>
                    <button class="w-full text-left p-2 text-sm hover:bg-slate-800 rounded transition-colors border border-transparent hover:border-slate-500 mb-1" onclick="checkAnswer(this, false)">To make API responses faster.</button>
                    <button class="w-full text-left p-2 text-sm hover:bg-slate-800 rounded transition-colors border border-transparent hover:border-slate-500 mb-1" onclick="checkAnswer(this, true)">To prevent invalid/corrupt data from being stored permanently.</button>
                    <button class="w-full text-left p-2 text-sm hover:bg-slate-800 rounded transition-colors border border-transparent hover:border-slate-500" onclick="checkAnswer(this, false)">To require users to provide more data than necessary.</button>
                </div>
            </div>
        </section>

    </main>

    <footer class="bg-slate-800 text-center p-4 text-xs text-slate-500 border-t border-slate-700">
        AP® is a trademark registered by the College Board, which is not affiliated with, and does not endorse, this product.
    </footer>

    <script>
        lucide.createIcons();

        // ===== QUIZ LOGIC =====
        function checkAnswer(btn, isCorrect) {
            const parent = btn.parentElement;
            const siblings = parent.querySelectorAll('button');
            siblings.forEach(s => {
                s.className = "w-full text-left p-2 text-sm rounded transition-colors border border-transparent mb-1 opacity-50";
            });
            if(isCorrect) {
                btn.className = "w-full text-left p-2 text-sm bg-green-900/50 text-green-200 border border-green-500 rounded font-bold mb-1";
                btn.innerText += " ✅ Correct";
            } else {
                btn.className = "w-full text-left p-2 text-sm bg-red-900/50 text-red-200 border border-red-500 rounded mb-1";
                btn.innerText += " ❌ Try again";
            }
        }

        // ===== MATCHING GAME LOGIC =====
        const gameData = [
            { request: "GET /api/match/data with JWT", endpoint: "Retrieve user's profile setup", pair: 0 },
            { request: "POST /api/match/setup with JWT", endpoint: "Initialize profile (409 if exists)", pair: 1 },
            { request: "POST /api/match/add with {index, data}", endpoint: "Add indexed data to profile", pair: 2 },
            { request: "POST /api/match/save-profile-json with array", endpoint: "Save quiz/game responses", pair: 3 },
            { request: "DELETE /api/match/add with {index}", endpoint: "Remove data from profile", pair: 4 }
        ];

        let gameState = {
            cards: [],
            selected: [],
            matches: 0,
            mistakes: 3,
            score: 0,
            gameOver: false,
            gameWon: false
        };

        function shuffleArray(arr) {
            return arr.sort(() => Math.random() - 0.5);
        }

        function initializeGame() {
            gameState = {
                cards: [],
                selected: [],
                matches: 0,
                mistakes: 3,
                score: 0,
                gameOver: false,
                gameWon: false
            };

            const allCards = [];
            gameData.forEach((item, idx) => {
                allCards.push({ id: idx, type: 'request', text: item.request, pair: item.pair });
                allCards.push({ id: idx + 100, type: 'endpoint', text: item.endpoint, pair: item.pair });
            });

            gameState.cards = shuffleArray(allCards);
            renderBoard();
            updateStats();
            document.getElementById('game-over').classList.add('hidden');
            document.getElementById('game-lost').classList.add('hidden');
            lucide.createIcons();
        }

        function renderBoard() {
            const board = document.getElementById('game-board');
            board.innerHTML = '';
            gameState.cards.forEach(card => {
                const cardEl = document.createElement('div');
                cardEl.className = 'bg-slate-700 hover:bg-slate-600 rounded-lg p-6 cursor-pointer transition-all border-2 border-slate-600 hover:border-blue-500 text-center slide-in';
                cardEl.style.minHeight = '120px';
                cardEl.style.display = 'flex';
                cardEl.style.alignItems = 'center';
                cardEl.style.justifyContent = 'center';
                
                const isSelected = gameState.selected.some(c => c.id === card.id);
                const isMatched = gameState.cards.filter(c => c.pair === card.pair && c.matched).length === 2;

                if(isMatched) {
                    cardEl.classList.add('opacity-50', 'cursor-default');
                    cardEl.style.pointerEvents = 'none';
                }

                if(isSelected) {
                    cardEl.classList.remove('bg-slate-700', 'hover:bg-slate-600', 'border-slate-600');
                    cardEl.classList.add('bg-blue-600', 'border-blue-400');
                }

                const content = document.createElement('div');
                content.innerHTML = `
                    <div class="text-xs text-slate-400 mb-2 uppercase">${card.type === 'request' ? '📨 Request' : '⚙️ Endpoint'}</div>
                    <div class="text-sm font-mono text-white break-words">${card.text}</div>
                `;
                cardEl.appendChild(content);
                cardEl.onclick = () => selectCard(card);
                board.appendChild(cardEl);
            });
        }

        function selectCard(card) {
            if(gameState.gameOver || gameState.gameWon) return;
            if(gameState.selected.some(c => c.id === card.id)) return;
            if(gameState.cards.find(c => c.id === card.id).matched) return;

            gameState.selected.push(card);
            renderBoard();

            if(gameState.selected.length === 2) {
                setTimeout(checkMatch, 500);
            }
        }

        function checkMatch() {
            const [card1, card2] = gameState.selected;
            const match = card1.pair === card2.pair && card1.type !== card2.type;

            if(match) {
                gameState.cards.forEach(c => {
                    if(c.id === card1.id || c.id === card2.id) {
                        c.matched = true;
                    }
                });
                gameState.matches++;
                gameState.score += 10;

                if(gameState.matches === gameData.length) {
                    gameState.gameWon = true;
                    document.getElementById('game-over').classList.remove('hidden');
                }
            } else {
                gameState.mistakes--;
                if(gameState.mistakes <= 0) {
                    gameState.gameOver = true;
                    document.getElementById('game-lost').classList.remove('hidden');
                }
            }

            gameState.selected = [];
            updateStats();
            renderBoard();
        }

        function updateStats() {
            document.getElementById('score').innerText = gameState.score;
            document.getElementById('mistakes').innerText = gameState.mistakes;
            document.getElementById('matches').innerText = `${gameState.matches}/${gameData.length}`;
        }

        function showHint() {
            if(gameState.gameOver || gameState.gameWon) return;
            alert('Hint: Match HTTP requests (left) with endpoints (right). Consider: HTTP method (GET/POST/DELETE), required data fields, and what the endpoint accomplishes. Remember: SETUP returns 409 if profile exists!');
        }

        // ===== SERVER INTEGRATION =====
        function getJWTFromCookie() {
            // Extract JWT from cookie (name: jwt_python_flask)
            const cookies = document.cookie.split(';');
            for(let cookie of cookies) {
                const [name, value] = cookie.trim().split('=');
                if(name === 'jwt_python_flask') {
                    return decodeURIComponent(value);
                }
            }
            return null;
        }

        async function checkServerStatus() {
            try {
                const token = getJWTFromCookie();
                if(!token) {
                    document.getElementById('status-text').innerText = 'No JWT cookie found - please log in';
                    document.getElementById('status-text').className = 'text-red-400';
                    return;
                }

                const response = await fetch('/api/match/data', {
                    method: 'GET',
                    headers: {
                        'Authorization': `Bearer ${token}`
                    },
                    credentials: 'include'  // Send cookies with request
                });
                
                if(response.ok) {
                    document.getElementById('status-text').innerText = 'Connected ✓';
                    document.getElementById('status-text').className = 'text-green-400';
                } else {
                    document.getElementById('status-text').innerText = 'Auth failed - Status: ' + response.status;
                    document.getElementById('status-text').className = 'text-orange-400';
                }
            } catch (error) {
                document.getElementById('status-text').innerText = 'Offline (will save when available)';
                document.getElementById('status-text').className = 'text-orange-400';
                console.error('Server check error:', error);
            }
        }

        async function saveProgress() {
            const token = getJWTFromCookie();
            if(!token) {
                alert('❌ No JWT cookie found. You must be logged in to save progress.');
                return;
            }

            const profileData = [
                { question: "endpoint_matching_game_score", response: gameState.score },
                { question: "endpoint_matching_game_matches", response: gameState.matches },
                { question: "endpoint_matching_game_completed", response: gameState.gameWon },
                { question: "endpoint_matching_game_timestamp", response: new Date().toISOString() }
            ];

            try {
                const response = await fetch('http://localhost:8401/api/match/save-profile-json', {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json',
                        'Authorization': `Bearer ${token}`
                    },
                    credentials: 'include',  // Send cookies with request
                    body: JSON.stringify({ profile_data: profileData })
                });

                const data = await response.json();

                if (response.ok) {
                    alert('✅ Game progress saved to server!');
                    console.log('Saved:', data);
                } else {
                    alert('❌ Failed to save. Status: ' + response.status + '\nMessage: ' + data.message);
                    console.error('Save error:', data);
                }
            } catch (error) {
                alert('❌ Error saving progress: ' + error.message);
                console.error('Network error:', error);
            }
        }