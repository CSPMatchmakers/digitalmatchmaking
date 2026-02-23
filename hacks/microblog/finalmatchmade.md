---
layout: opencs
title: Matchmade
description: The final module where the additions to your profile link you up to people with similar tastes.
permalink: /matchmade/
author: Adhav S
---

<style>
    body {
        min-height: 100vh;
        background: linear-gradient(135deg, #0a0e27 0%, #1a1a3e 50%, #0d1b2a 100%);
        background-attachment: fixed;
        font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        color: #e0e0e0;
        margin: 0;
        padding: 20px;
        position: relative;
        overflow-x: hidden;
    }

    body::before {
        content: '';
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: 
            repeating-linear-gradient(
                0deg,
                rgba(0, 255, 200, 0.03) 0px,
                rgba(0, 255, 200, 0.03) 1px,
                transparent 1px,
                transparent 2px
            ),
            repeating-linear-gradient(
                90deg,
                rgba(0, 255, 200, 0.02) 0px,
                rgba(0, 255, 200, 0.02) 1px,
                transparent 1px,
                transparent 2px
            );
        pointer-events: none;
        z-index: 1;
        animation: scanlines 8s linear infinite;
    }

    @keyframes scanlines {
        0% { transform: translateY(0); }
        100% { transform: translateY(10px); }
    }

    body::after {
        content: '';
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: 
            radial-gradient(circle at 20% 50%, rgba(0, 255, 200, 0.1) 0%, transparent 50%),
            radial-gradient(circle at 80% 80%, rgba(102, 126, 234, 0.1) 0%, transparent 50%);
        pointer-events: none;
        z-index: 0;
    }

    .matchmaking-container {
        max-width: 1200px;
        margin: 0 auto;
    }

    .header {
        text-align: center;
        margin-bottom: 2em;
    }

    .header h1 {
        font-size: 2.5em;
        color: #667eea;
        margin: 0 0 0.5em 0;
    }

    .header p {
        color: #b0b0b0;
        font-size: 2em;
        font-weight: 600;
        margin-bottom: 0.5em;
    }
    .header-bar {
        width: 100%;
        height: 6px;
        background: linear-gradient(90deg, #667eea 0%, #8b9dff 100%);
        border-radius: 3px;
        margin-bottom: 2em;
        box-shadow: 0 2px 8px rgba(102,126,234,0.15);
    }

    /* ====== Edit Button & Preferences Panel ====== */
    .edit-btn-wrapper {
        display: flex;
        justify-content: flex-end;
        margin-bottom: 1em;
    }

    .btn-edit {
        background: linear-gradient(135deg, #4a4a6a, #3a3a5a);
        color: #8b9dff;
        border: 2px solid rgba(102, 126, 234, 0.5);
        border-radius: 8px;
        padding: 0.6em 1.4em;
        font-size: 0.95em;
        font-weight: bold;
        cursor: pointer;
        letter-spacing: 1px;
        text-transform: uppercase;
        transition: all 0.3s;
        display: flex;
        align-items: center;
        gap: 0.5em;
    }

    .btn-edit:hover {
        background: linear-gradient(135deg, #667eea, #5568d3);
        color: white;
        border-color: #667eea;
        box-shadow: 0 4px 15px rgba(102, 126, 234, 0.4);
        transform: translateY(-2px);
    }

    .preferences-panel {
        background: rgba(20, 20, 40, 0.97);
        border: 2px solid rgba(102, 126, 234, 0.5);
        border-radius: 12px;
        padding: 1.8em;
        margin-bottom: 1.5em;
        display: none;
        animation: slideDown 0.3s ease;
        box-shadow: 0 8px 32px rgba(0,0,0,0.4);
    }

    .preferences-panel.open {
        display: block;
    }

    @keyframes slideDown {
        from { opacity: 0; transform: translateY(-10px); }
        to   { opacity: 1; transform: translateY(0); }
    }

    .preferences-panel h3 {
        color: #8b9dff;
        font-size: 1.15em;
        margin: 0 0 1.2em 0;
        border-bottom: 2px solid rgba(102, 126, 234, 0.3);
        padding-bottom: 0.5em;
    }

    .prefs-grid {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        gap: 1em;
        margin-bottom: 1.2em;
    }

    @media (max-width: 768px) {
        .prefs-grid { grid-template-columns: 1fr; }
    }

    .pref-group label {
        display: block;
        color: #b0b0b0;
        font-weight: 600;
        margin-bottom: 0.4em;
        font-size: 0.9em;
    }

    .pref-group select {
        width: 100%;
        padding: 0.7em;
        background: rgba(20, 20, 35, 0.8);
        border: 2px solid rgba(102, 126, 234, 0.3);
        border-radius: 8px;
        color: #e0e0e0;
        font-size: 0.95em;
        transition: all 0.3s;
    }

    .pref-group select:focus {
        outline: none;
        border-color: #667eea;
        box-shadow: 0 0 10px rgba(102, 126, 234, 0.3);
    }

    .prefs-actions {
        display: flex;
        gap: 0.8em;
        justify-content: flex-end;
    }

    .btn-save-prefs {
        background: linear-gradient(135deg, #667eea, #8b9dff);
        color: white;
        border: none;
        border-radius: 8px;
        padding: 0.65em 1.5em;
        font-size: 0.95em;
        font-weight: bold;
        cursor: pointer;
        text-transform: uppercase;
        letter-spacing: 1px;
        transition: all 0.3s;
    }

    .btn-save-prefs:hover {
        transform: translateY(-2px);
        box-shadow: 0 6px 20px rgba(102, 126, 234, 0.5);
    }

    .btn-cancel-prefs {
        background: transparent;
        color: #888;
        border: 2px solid rgba(102,126,234,0.2);
        border-radius: 8px;
        padding: 0.65em 1.5em;
        font-size: 0.95em;
        font-weight: bold;
        cursor: pointer;
        text-transform: uppercase;
        letter-spacing: 1px;
        transition: all 0.3s;
    }

    .btn-cancel-prefs:hover {
        color: #e0e0e0;
        border-color: rgba(102,126,234,0.5);
    }

    /* Preferences indicator badge */
    .pref-badge {
        display: inline-block;
        background: rgba(102, 126, 234, 0.2);
        border: 1px solid rgba(102, 126, 234, 0.4);
        border-radius: 12px;
        padding: 0.25em 0.7em;
        font-size: 0.75em;
        color: #8b9dff;
        margin-left: 0.5em;
        font-weight: normal;
        vertical-align: middle;
    }

    /* ====== Compatibility Score Banner ====== */
    .compat-banner {
        display: flex;
        align-items: center;
        justify-content: space-between;
        background: linear-gradient(135deg, rgba(26,26,62,0.9), rgba(13,27,42,0.9));
        border: 2px solid #667eea;
        border-radius: 12px;
        padding: 1.2em 1.8em;
        margin-bottom: 1.5em;
        gap: 1.5em;
    }

    .compat-label {
        color: #b0b0b0;
        font-weight: 600;
        font-size: 1em;
        letter-spacing: 1px;
        text-transform: uppercase;
        white-space: nowrap;
    }

    .compat-bar-wrap {
        flex: 1;
        height: 14px;
        background: rgba(42, 42, 64, 0.8);
        border-radius: 7px;
        overflow: hidden;
        box-shadow: inset 0 2px 4px rgba(0,0,0,0.5);
    }

    .compat-bar-fill {
        height: 100%;
        border-radius: 7px;
        transition: width 0.8s ease;
        box-shadow: 0 0 10px rgba(102, 126, 234, 0.6);
    }

    .compat-pct {
        font-size: 1.8em;
        font-weight: bold;
        min-width: 70px;
        text-align: right;
        white-space: nowrap;
    }

    .compat-breakdown {
        font-size: 0.82em;
        color: #888;
        white-space: nowrap;
    }

    /* ====== Card ====== */
    .card {
        background: rgba(30, 30, 46, 0.95);
        border: 2px solid rgba(102, 126, 234, 0.4);
        border-radius: 12px;
        padding: 2em;
        margin-bottom: 2em;
        backdrop-filter: blur(10px);
        box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
    }

    .stats-bar {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        gap: 1em;
        margin-bottom: 2em;
    }

    .stat-box {
        background: linear-gradient(135deg, #2a2a40, #1f1f35);
        border: 2px solid #667eea;
        border-radius: 12px;
        padding: 1.8em 1.2em;
        text-align: center;
        min-width: 140px;
        min-height: 90px;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        font-size: 1.1em;
        box-shadow: 0 4px 16px rgba(102, 126, 234, 0.10);
    }

    .stat-value {
        font-size: 2.2em;
        font-weight: bold;
        color: #8b9dff;
        margin-bottom: 0.2em;
    }

    .stat-label {
        color: #b0b0b0;
        margin-top: 0.3em;
        font-size: 1em;
        font-weight: 600;
        letter-spacing: 1px;
    }

    /* Comparison Table */
    .comparison-table {
        background: linear-gradient(135deg, rgba(26, 26, 62, 0.6), rgba(13, 27, 42, 0.6));
        border: 2px solid #667eea;
        border-radius: 12px;
        padding: 1.5em;
        margin-bottom: 2em;
        overflow-x: auto;
    }

    table {
        width: 100%;
        border-collapse: collapse;
    }

    thead {
        background: linear-gradient(135deg, #3a3a52, #2d2d42);
    }

    th {
        color: #8b9dff;
        padding: 1.2em;
        text-align: left;
        font-weight: bold;
        text-transform: uppercase;
        letter-spacing: 1px;
        font-size: 0.85em;
        border-bottom: 3px solid #667eea;
    }

    tbody tr {
        border-bottom: 1px solid rgba(102, 126, 234, 0.2);
        transition: all 0.3s ease;
    }

    tbody tr:hover {
        background: rgba(102, 126, 234, 0.15);
    }

    td {
        padding: 1.2em;
        color: #e0e0e0;
    }

    .attribute-name {
        font-weight: bold;
        color: #8b9dff;
        min-width: 140px;
    }

    .your-value {
        background: rgba(102, 126, 234, 0.1);
        border-left: 3px solid #667eea;
        padding: 1em;
        border-radius: 4px;
    }

    .their-value {
        background: rgba(102, 126, 234, 0.1);
        border-left: 3px solid #667eea;
        padding: 1em;
        border-radius: 4px;
    }

    .match-status {
        text-align: center;
        font-weight: bold;
        font-size: 1.3em;
    }

    .match-status.match {
        color: #27ae60;
    }

    .match-status.mismatch {
        color: #e74c3c;
    }

    /* Action Buttons */
    .btn {
        flex: 1;
        padding: 1.3em;
        border: none;
        border-radius: 10px;
        font-size: 1.1em;
        font-weight: bold;
        cursor: pointer;
        transition: all 0.3s;
        text-transform: uppercase;
        letter-spacing: 1.5px;
        box-shadow: 0 4px 15px rgba(0, 0, 0, 0.3);
    }

    .btn-primary {
        background: linear-gradient(135deg, #667eea, #8b9dff);
        color: white;
    }

    .btn-primary:hover:not(:disabled) {
        transform: translateY(-4px);
        box-shadow: 0 8px 25px rgba(102, 126, 234, 0.5);
    }

    .btn-match {
        background: linear-gradient(135deg, #27ae60, #229954);
        color: white;
    }

    .btn-match:hover:not(:disabled) {
        transform: translateY(-4px);
        box-shadow: 0 8px 25px rgba(39, 174, 96, 0.5);
    }

    .btn-skip {
        background: linear-gradient(135deg, #667eea, #5568d3);
        color: white;
    }

    .btn-skip:hover:not(:disabled) {
        transform: translateY(-4px);
        box-shadow: 0 8px 25px rgba(102, 126, 234, 0.5);
    }

    .btn:disabled {
        opacity: 0.5;
        cursor: not-allowed;
    }

    .button-group {
        display: flex;
        gap: 1em;
        margin-top: 2em;
    }

    .loading {
        text-align: center;
        padding: 3em;
    }

    .spinner {
        border: 4px solid rgba(102, 126, 234, 0.3);
        border-top: 4px solid #667eea;
        border-radius: 50%;
        width: 50px;
        height: 50px;
        animation: spin 1s linear infinite;
        margin: 0 auto 1em;
    }

    @keyframes spin {
        0% { transform: rotate(0deg); }
        100% { transform: rotate(360deg); }
    }

    .error-message {
        background: rgba(231, 76, 60, 0.2);
        border: 2px solid #e74c3c;
        color: #ff9999;
        padding: 1.5em;
        border-radius: 8px;
        text-align: center;
    }

    .finish-screen {
        text-align: center;
        padding: 2em 0;
    }

    .finish-screen h2 {
        color: #667eea;
        font-size: 2em;
    }

    .matches-grid {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
        gap: 2em;
        margin-top: 2em;
    }

    .match-card {
        background: linear-gradient(135deg, #2a2a40 0%, #1f1f35 100%);
        border: 2px solid #27ae60;
        border-radius: 12px;
        padding: 2em;
        transition: all 0.3s;
    }

    .match-card:hover {
        transform: translateY(-6px);
        box-shadow: 0 12px 35px rgba(39, 174, 96, 0.3);
        border-color: #51cf66;
    }

    .match-card h4 {
        color: #8b9dff;
        margin: 0 0 0.8em 0;
        font-size: 1.2em;
    }

    .match-card .compatibility-percent {
        color: #27ae60;
        font-weight: bold;
        font-size: 1.3em;
    }

    @media (max-width: 768px) {
        .stats-bar {
            grid-template-columns: 1fr;
        }

        .comparison-table {
            padding: 1em;
        }

        th, td {
            padding: 0.8em;
            font-size: 0.9em;
        }

        .compat-banner {
            flex-wrap: wrap;
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
    }
</style>

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

<div class="matchmaking-container">
    <div class="header">
        <h1>Profile Matcher</h1>
        <p>Discover Compatible Connections</p>
        <div class="header-bar"></div>
    </div>

    <!-- ====== EDIT BUTTON & PREFERENCES PANEL ====== -->
    <div class="edit-btn-wrapper">
        <button class="btn-edit" id="editPrefsBtn" onclick="window.togglePreferences()">
            ✏️ Edit Preferences
        </button>
    </div>

    <div class="preferences-panel" id="preferencesPanel">
        <h3>🧠 Matching Preferences <span class="pref-badge" id="prefStatus">Not Set</span></h3>
        <div class="prefs-grid">
            <div class="pref-group">
                <label>Decision-making style</label>
                <select id="prefDecision">
                    <option value="">Select...</option>
                    <option value="Logical">Logical — Data-driven</option>
                    <option value="Intuitive">Intuitive — Feeling-based</option>
                </select>
            </div>
            <div class="pref-group">
                <label>Lifestyle preference</label>
                <select id="prefLifestyle">
                    <option value="">Select...</option>
                    <option value="Organized">Organized — Structured</option>
                    <option value="Spontaneous">Spontaneous — Flexible</option>
                </select>
            </div>
            <div class="pref-group">
                <label>Social style</label>
                <select id="prefSocial">
                    <option value="">Select...</option>
                    <option value="Introvert">Introvert — Small groups</option>
                    <option value="Extrovert">Extrovert — Enjoy crowds</option>
                </select>
            </div>
        </div>
        <div class="prefs-actions">
            <button class="btn-cancel-prefs" onclick="window.cancelPreferences()">Cancel</button>
            <button class="btn-save-prefs" onclick="window.savePreferences()">Save &amp; Apply</button>
        </div>
    </div>
    <!-- ====== END PREFERENCES PANEL ====== -->

    <div class="card">
        <div id="mainContent">
            <div class="loading">
                <div class="spinner"></div>
                <p>Loading profiles...</p>
            </div>
        </div>
    </div>
</div>

<script type="module">
    import { pythonURI } from '{{site.baseurl}}/assets/js/api/config.js';

    let state = {
        currentUserProfile: null,
        currentUserUID: null,
        allProfiles: [],
        currentIndex: 0,
        matches: [],
        skipped: [],
        initialized: false,
        usernameCycleIndex: 0,
        userPreferences: null
    };

    // ============================================================
    //  PREFERENCES PANEL TOGGLE
    // ============================================================
    window.togglePreferences = function() {
        const panel = document.getElementById('preferencesPanel');
        const isOpen = panel.classList.contains('open');
        if (isOpen) {
            panel.classList.remove('open');
        } else {
            // Pre-fill selects from saved state
            if (state.userPreferences) {
                document.getElementById('prefDecision').value  = state.userPreferences.decision  || '';
                document.getElementById('prefLifestyle').value = state.userPreferences.lifestyle || '';
                document.getElementById('prefSocial').value    = state.userPreferences.social    || '';
            }
            panel.classList.add('open');
        }
    };

    window.cancelPreferences = function() {
        document.getElementById('preferencesPanel').classList.remove('open');
    };

    window.savePreferences = function() {
        const decision  = document.getElementById('prefDecision').value;
        const lifestyle = document.getElementById('prefLifestyle').value;
        const social    = document.getElementById('prefSocial').value;

        if (!decision || !lifestyle || !social) {
            alert('Please fill in all three preferences before saving.');
            return;
        }

        state.userPreferences = { decision, lifestyle, social };
        document.getElementById('prefStatus').textContent = 'Active';
        document.getElementById('prefStatus').style.background = 'rgba(39,174,96,0.25)';
        document.getElementById('prefStatus').style.borderColor = 'rgba(39,174,96,0.5)';
        document.getElementById('prefStatus').style.color = '#27ae60';
        document.getElementById('preferencesPanel').classList.remove('open');

        // Re-render current card so score updates immediately
        if (state.initialized) showCurrentProfile();
    };

    // ============================================================
    //  INIT
    // ============================================================
    async function initMatchmaking() {
        try {
            const userResponse = await fetch(`${pythonURI}/api/match/data`, {
                method: 'GET',
                credentials: 'include',
                headers: { 'Content-Type': 'application/json' }
            });

            if (!userResponse.ok) throw new Error(`User profile error: ${userResponse.status}`);

            const userData = await userResponse.json();
            if (!userData.data) throw new Error('No profile data found');
            state.currentUserProfile = userData.data;
            state.currentUserUID = userData.uid || 'current_user';

            const allResponse = await fetch(`${pythonURI}/api/match/all-data`, {
                method: 'GET',
                credentials: 'include',
                headers: { 'Content-Type': 'application/json' }
            });

            if (!allResponse.ok) throw new Error(`Profiles error: ${allResponse.status}`);

            const allData = await allResponse.json();
            if (!allData.users || !Array.isArray(allData.users)) throw new Error('Invalid profile data format');

            state.allProfiles = allData.users
                .filter(p => p.uid !== state.currentUserUID && p.data && Object.keys(p.data).length > 0)
                .map(p => ({ ...p, uid: p.uid }));

            if (state.allProfiles.length === 0) {
                showNoProfiles();
            } else {
                state.initialized = true;
                showCurrentProfile();
            }
        } catch (error) {
            console.error('Detailed error:', error);
            showError(`Failed to fetch profiles: ${error.message}`);
        }
    }

    // ============================================================
    //  COMPATIBILITY ALGORITHM
    //  Personality score: based on how many of the 3 trait pairs
    //  match — gives 0%, 33%, 67%, or 100% of the personality
    //  portion (60 pts max).  Remaining 40 pts from profile fields.
    // ============================================================
    function calculateCompatibility(profile1, profile2) {
        const matches    = [];
        const mismatches = [];
        let fieldScore   = 0;

        // ---- Profile-field scoring (40 pts max) ----
        const fields = ['age', 'location', 'interests', 'hobbies', 'occupation', 'relationship_type', 'mbti'];

        fields.forEach(field => {
            const val1 = profile1[field];
            const val2 = profile2[field];
            if (!val1 || !val2) return;

            const v1 = String(val1).toLowerCase().trim();
            const v2 = String(val2).toLowerCase().trim();

            if (v1 === v2) {
                matches.push({ field, value1: val1, value2: val2 });
                fieldScore += 5;
            } else if (field === 'age') {
                const age1 = parseInt(v1);
                const age2 = parseInt(v2);
                if (!isNaN(age1) && !isNaN(age2)) {
                    const diff = Math.abs(age1 - age2);
                    if (diff <= 3) {
                        matches.push({ field, value1: val1, value2: val2 });
                        fieldScore += 4;
                    } else if (diff <= 8) {
                        matches.push({ field, value1: val1, value2: val2 });
                        fieldScore += 2;
                    } else {
                        mismatches.push({ field, value1: val1, value2: val2 });
                    }
                }
            } else if (field === 'interests' || field === 'hobbies') {
                const arr1 = Array.isArray(val1) ? val1 : [val1];
                const arr2 = Array.isArray(val2) ? val2 : [val2];
                const commonCount = arr1.filter(i =>
                    arr2.some(j => String(i).toLowerCase() === String(j).toLowerCase())
                ).length;
                if (commonCount > 0) {
                    matches.push({ field, value1: commonCount, value2: `shared ${field}` });
                    fieldScore += Math.min(commonCount * 3, 5);
                } else {
                    mismatches.push({ field, value1: arr1[0], value2: arr2[0] });
                }
            } else {
                mismatches.push({ field, value1: val1, value2: val2 });
            }
        });

        const cappedFieldScore = Math.min(fieldScore, 40);

        // ---- Personality trait scoring (60 pts max) ----
        // Determine whose personality to compare:
        //   - "Your" side: userPreferences if set, else profile1.profile_quiz traits
        //   - "Their" side: profile2.profile_quiz traits
        const yourTraits  = state.userPreferences
            ? {
                decision:  state.userPreferences.decision,
                lifestyle: state.userPreferences.lifestyle,
                social:    state.userPreferences.social
              }
            : (profile1.profile_quiz?.analysis?.personalityTraits || {});

        const theirTraits = profile2.profile_quiz?.analysis?.personalityTraits || {};

        const traitKeys      = ['decision', 'lifestyle', 'social'];
        let traitMatchCount  = 0;
        let traitTotal       = 0;

        traitKeys.forEach(trait => {
            const yourVal  = yourTraits[trait];
            const theirVal = theirTraits[trait];
            if (!yourVal || !theirVal) return;
            traitTotal++;
            if (String(yourVal).toLowerCase() === String(theirVal).toLowerCase()) {
                traitMatchCount++;
                matches.push({ field: `${trait}_personality`, value1: yourVal, value2: theirVal });
            } else {
                mismatches.push({ field: `${trait}_personality`, value1: yourVal, value2: theirVal });
            }
        });

        // Personality score: proportion of matched traits × 60
        const personalityScore = traitTotal > 0
            ? Math.round((traitMatchCount / traitTotal) * 60)
            : 0;

        const finalScore = Math.min(cappedFieldScore + personalityScore, 100);

        return {
            score: finalScore,
            matches,
            mismatches,
            traitMatchCount,
            traitTotal,
            personalityScore,
            fieldScore: cappedFieldScore
        };
    }

    // ============================================================
    //  COMPATIBILITY BANNER
    // ============================================================
    function buildCompatBanner(compat) {
        const pct   = compat.score;
        let color;
        if (pct >= 70)      color = '#27ae60';
        else if (pct >= 40) color = '#f39c12';
        else                color = '#e74c3c';

        const traitNote = compat.traitTotal > 0
            ? `${compat.traitMatchCount}/${compat.traitTotal} personality traits match`
            : 'No personality data yet — set preferences above';

        return `
            <div class="compat-banner">
                <span class="compat-label">Compatibility</span>
                <div class="compat-bar-wrap">
                    <div class="compat-bar-fill"
                         style="width:${pct}%; background: linear-gradient(90deg, ${color}, ${color}cc);"></div>
                </div>
                <div>
                    <div class="compat-pct" style="color:${color};">${pct}%</div>
                    <div class="compat-breakdown">${traitNote}</div>
                </div>
            </div>
        `;
    }

    // ============================================================
    //  BUILD COMPARISON TABLE ROWS
    // ============================================================
    function buildComparisonTable(yourProfile, theirProfile) {
        const username = 'You';
        const usernameCycle = [
            'indy', 'salem', 'phoenix', 'cody', 'pixel', 'cadence', 'ace', 'marco', 'libra', 'nikola', 'isaac', 'madam', 'flash', 'parker', 'merlin',
            'sky', 'toby', 'hop', 'niko', 'K9',
            'thisisasupercooluser', 'testuser2', 'testuser67676767', 'testusersixtyseven', 'Matching', 'aoisfoi', 'Timothee Chalamat', 'Drake "Drake Maye" Maye', 'shreksswamp', 'StinkyJoe', 'dr pooglarth', 'tester', 'Morttt', 'Elamkulam Manakkal Sankaran Namboodiripad', 'george washington'
        ];
        const theirusername = usernameCycle[state.usernameCycleIndex % usernameCycle.length];

        // Decide which personality values to show for "your" side
        const yourTraits = state.userPreferences
            ? {
                decision:  state.userPreferences.decision,
                lifestyle: state.userPreferences.lifestyle,
                social:    state.userPreferences.social
              }
            : (yourProfile?.profile_quiz?.analysis?.personalityTraits || {});

        const theirTraits = theirProfile?.profile_quiz?.analysis?.personalityTraits || {};

        let rows = '';

        rows += `
            <tr>
                <td class="attribute-name">Username</td>
                <td class="your-value">${formatValue(username)}</td>
                <td class="match-status" style="color:#ffd700; font-size:1.5em;">~</td>
                <td class="their-value">${formatValue(theirusername)}</td>
            </tr>
        `;

        rows += `
            <tr>
                <td colspan="4" style="text-align:center; font-weight:bold; color:#8b9dff; background:rgba(102,126,234,0.08);">
                    Personality Traits
                    ${state.userPreferences ? '<span style="font-size:0.75em; color:#27ae60; margin-left:0.5em;">(from your preferences)</span>' : ''}
                </td>
            </tr>
        `;

        const traitList = ['decision', 'lifestyle', 'social'];
        traitList.forEach(trait => {
            const yourVal  = yourTraits[trait]  !== undefined ? yourTraits[trait]  : 'Not specified';
            const theirVal = theirTraits[trait] !== undefined ? theirTraits[trait] : 'Not specified';
            const isMatch  = yourVal !== 'Not specified' && theirVal !== 'Not specified'
                          && String(yourVal).toLowerCase() === String(theirVal).toLowerCase();
            rows += `
                <tr>
                    <td class="attribute-name">${formatFieldName(trait)}</td>
                    <td class="your-value">${formatValue(yourVal)}</td>
                    <td class="match-status ${isMatch ? 'match' : 'mismatch'}" style="font-size:1.5em;">
                        ${isMatch
                            ? '<span style="color:#27ae60;">✓</span>'
                            : '<span style="color:#e74c3c;">✗</span>'}
                    </td>
                    <td class="their-value">${formatValue(theirVal)}</td>
                </tr>
            `;
        });

        return rows;
    }

    // ============================================================
    //  SHOW CURRENT PROFILE
    // ============================================================
    function showCurrentProfile() {
        if (state.currentIndex >= state.allProfiles.length) {
            showResults();
            return;
        }

        const profile    = state.allProfiles[state.currentIndex];
        const compat     = calculateCompatibility(state.currentUserProfile, profile.data);
        const tableRows  = buildComparisonTable(state.currentUserProfile, profile.data);
        const compatHTML = buildCompatBanner(compat);

        const content = document.getElementById('mainContent');
        content.innerHTML = `
            <div class="stats-bar">
                <div class="stat-box">
                    <div class="stat-value">${state.matches.length}</div>
                    <div class="stat-label">Matches</div>
                </div>
                <div class="stat-box">
                    <div class="stat-value">${state.currentIndex + 1}/${state.allProfiles.length}</div>
                    <div class="stat-label">Profile</div>
                </div>
                <div class="stat-box">
                    <div class="stat-value">${state.skipped.length}</div>
                    <div class="stat-label">Skipped</div>
                </div>
            </div>

            ${compatHTML}

            <div class="comparison-table">
                <table>
                    <thead>
                        <tr>
                            <th>Attribute</th>
                            <th>Your Profile</th>
                            <th>Match</th>
                            <th>${formatValue(profile.data.name || 'Their Profile')}</th>
                        </tr>
                    </thead>
                    <tbody>
                        ${tableRows}
                    </tbody>
                </table>
            </div>

            <div class="button-group">
                <button class="btn btn-skip" onclick="window.handleSkip()">Skip</button>
                <button class="btn btn-match" onclick="window.handleMatch()">Match</button>
            </div>
        `;
    }

    // ============================================================
    //  HELPERS
    // ============================================================
    function formatFieldName(field) {
        return field.replace(/_/g, ' ').replace(/\b\w/g, l => l.toUpperCase());
    }

    function formatValue(value) {
        if (Array.isArray(value)) return value.join(', ');
        if (value && typeof value === 'object') {
            return Object.entries(value)
                .map(([k, v]) => `${formatFieldName(k)}: ${formatValue(v)}`)
                .join(', ');
        }
        return value || 'Not specified';
    }

    // ============================================================
    //  MATCH / SKIP
    // ============================================================
    async function handleMatch() {
        const profile    = state.allProfiles[state.currentIndex];
        const compat     = calculateCompatibility(state.currentUserProfile, profile.data);
        state.matches.push({ ...profile, compatibility: compat.score });

        try {
            const existingMatches = state.currentUserProfile.matched_with || [];
            const updated = Array.isArray(existingMatches) ? existingMatches : [existingMatches];
            if (!updated.includes(profile.uid)) updated.push(profile.uid);

            await fetch(`${pythonURI}/api/match/add`, {
                method: 'POST',
                credentials: 'include',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify({ index: 'matched_with', data: updated })
            });
        } catch (error) {
            console.error('Error saving match:', error);
        }

        state.currentIndex++;
        state.usernameCycleIndex++;
        showCurrentProfile();
    }

    function handleSkip() {
        state.skipped.push(state.allProfiles[state.currentIndex]);
        state.currentIndex++;
        state.usernameCycleIndex++;
        showCurrentProfile();
    }

    window.handleMatch = handleMatch;
    window.handleSkip  = handleSkip;

    // ============================================================
    //  RESULTS SCREEN
    // ============================================================
    function showResults() {
        const content = document.getElementById('mainContent');

        const reviewedText = state.allProfiles.length === 1
            ? `You've reviewed the only available profile`
            : `You've completed reviewing all ${state.allProfiles.length} available profiles`;

        const congratsMessage = state.matches.length > 0
            ? `Congratulations! You found <strong>${state.matches.length}</strong> potential connection${state.matches.length !== 1 ? 's' : ''}!`
            : `You've reached the end of all available profiles. No matches this round — don't give up!`;

        content.innerHTML = `
            <div class="finish-screen">
                <h2>Matching Complete!</h2>
                <p style="color:#8b9dff; font-size:1.2em; font-weight:500; margin:1.5em 0;">${reviewedText}</p>
                <p style="color:#27ae60; font-size:1.3em; font-weight:bold; margin:1.5em 0; padding:1.5em;
                          background:rgba(39,174,96,0.1); border-radius:8px; border:2px solid #27ae60;">
                    ${congratsMessage}
                </p>

                <div class="stats-bar" style="margin:2em 0; justify-content:center; display:flex; gap:2em;">
                    <div class="stat-box">
                        <div class="stat-value">${state.matches.length}</div>
                        <div class="stat-label">Total Matches</div>
                    </div>
                    <div class="stat-box">
                        <div class="stat-value">${state.skipped.length}</div>
                        <div class="stat-label">Skipped</div>
                    </div>
                </div>

                ${state.matches.length > 0 ? `
                    <h3 style="color:#8b9dff; margin-top:2em;">Your Matches</h3>
                    <div class="matches-grid">
                        ${state.matches.map(m => `
                            <div class="match-card">
                                <h4>${formatValue(m.data.name || m.uid)}</h4>
                                <p style="color:#c0c0c0; margin:0.5em 0;">Somewhere on Earth</p>
                                <p class="compatibility-percent">${m.compatibility}% Compatible</p>
                            </div>
                        `).join('')}
                    </div>
                ` : `
                    <div style="background:rgba(102,126,234,0.1); padding:2em; border-radius:8px; margin-top:2em; border:2px dashed #667eea;">
                        <p style="color:#b0b0b0;">No matches this round. Try again to find your perfect match!</p>
                    </div>
                `}

                <div class="button-group" style="margin-top:2em;">
                    <button class="btn btn-skip" onclick="location.reload()">Start Over</button>
                </div>
            </div>
        `;
    }

    function showNoProfiles() {
        document.getElementById('mainContent').innerHTML = `
            <div class="error-message">
                <h3>No Profiles Available</h3>
                <p>Complete your profile first before matching with others!</p>
            </div>`;
    }

    function showError(message) {
        document.getElementById('mainContent').innerHTML = `
            <div class="error-message">
                <h3>Error</h3>
                <p>${message}</p>
            </div>`;
    }

    // ============================================================
    //  BOOTSTRAP — load profiles immediately (no gate form)
    // ============================================================
    initMatchmaking();

    // ============================================================
    //  PAGE NAVIGATION SYSTEM
    // ============================================================
    const VISITED_KEY = 'api_visited_pages';
    let visitedPages  = {};

    const pages = [
        { id: 1, url: '/digitalmatchmaking/api/' },
        { id: 2, url: '/digitalmatchmaking/mcq/' },
        { id: 3, url: '/digitalmatchmaking/microb/' },
        { id: 4, url: '/digitalmatchmaking/bio_create/' },
        { id: 5, url: '/digitalmatchmaking/matchmade/' }
    ];

    function loadVisitedPages() {
        try { return JSON.parse(localStorage.getItem(VISITED_KEY)) || {}; }
        catch (e) { return {}; }
    }

    function saveVisitedPages() {
        try { localStorage.setItem(VISITED_KEY, JSON.stringify(visitedPages)); }
        catch (e) {}
    }

    function isPageUnlocked(pageId) {
        if (pageId === 1) return true;
        if (!window.hasAccount) return false;
        return visitedPages[pageId - 1];
    }

    function markPageVisited(pageId) {
        visitedPages[pageId] = true;
        saveVisitedPages();
        updateNavigation();
    }

    function updateNavigation() {
        const navNodes      = document.querySelectorAll('.nav-node');
        const navConnectors = document.querySelectorAll('.nav-connector');

        navNodes.forEach((node, idx) => {
            const pageId = idx + 1;
            node.classList.remove('locked', 'unlocked', 'visited', 'current');

            if (visitedPages[pageId]) {
                node.classList.add('visited');
                node.href = node.dataset.url;
                node.style.cursor = 'pointer';
                node.onclick = function() { window.location.href = this.dataset.url; };
            } else if (isPageUnlocked(pageId)) {
                node.classList.add('unlocked');
                node.href = node.dataset.url;
                node.style.cursor = 'pointer';
                node.onclick = function() { markPageVisited(pageId); window.location.href = this.dataset.url; };
            } else {
                node.classList.add('locked');
                node.style.cursor = 'not-allowed';
                node.href = 'javascript:void(0)';
                node.onclick = null;
            }
        });

        navConnectors.forEach((conn, idx) => {
            if (visitedPages[idx + 1]) conn.classList.add('visited');
            else conn.classList.remove('visited');
        });

        const currentUrl = window.location.pathname;
        navNodes.forEach(node => {
            if (node.dataset.url === currentUrl) node.classList.add('current');
        });
    }

    visitedPages = loadVisitedPages();
    pages.forEach(page => {
        if (page.url === window.location.pathname) markPageVisited(page.id);
    });
    updateNavigation();
</script>