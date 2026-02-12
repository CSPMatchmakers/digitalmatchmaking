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

    /* Compatibility Section */
    .compatibility-section {
        background: linear-gradient(135deg, #3a3a52 0%, #2d2d42 100%);
        border: 2px solid #667eea;
        border-radius: 12px;
        padding: 2.5em;
        margin-bottom: 2em;
    }

    .compatibility-header {
        text-align: center;
        margin-bottom: 2em;
    }

    .compatibility-score {
        display: flex;
        align-items: center;
        justify-content: center;
        gap: 2em;
        margin-bottom: 1.5em;
    }

    .score-circle {
        width: 140px;
        height: 140px;
        border-radius: 50%;
        background: conic-gradient(#667eea 0%, #667eea var(--score), rgba(102, 126, 234, 0.2) var(--score), rgba(102, 126, 234, 0.2) 100%);
        display: flex;
        align-items: center;
        justify-content: center;
        box-shadow: 0 8px 30px rgba(102, 126, 234, 0.3);
        animation: pulse 2s ease-in-out infinite;
    }

    @keyframes pulse {
        0%, 100% { box-shadow: 0 8px 30px rgba(102, 126, 234, 0.3); }
        50% { box-shadow: 0 8px 40px rgba(102, 126, 234, 0.6); }
    }

    .score-number {
        font-size: 2.8em;
        font-weight: bold;
        color: #667eea;
    }

    .score-label {
        color: #b0b0b0;
        font-size: 1em;
        margin-top: 0.5em;
        text-align: center;
    }

    .compatibility-bar {
        width: 100%;
        height: 16px;
        background: #2a2a40;
        border-radius: 8px;
        overflow: hidden;
        margin-bottom: 2em;
        box-shadow: inset 0 2px 4px rgba(0, 0, 0, 0.5);
    }

    .compatibility-fill {
        height: 100%;
        background: linear-gradient(90deg, #667eea, #8b9dff);
        transition: width 0.8s ease;
        border-radius: 8px;
        box-shadow: 0 0 10px rgba(102, 126, 234, 0.6);
    }

    .compatibility-details {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 2em;
    }

    .detail-group {
        background: rgba(0, 0, 0, 0.3);
        border-radius: 10px;
        padding: 1.5em;
        border-top: 4px solid #667eea;
    }

    .detail-group.matches {
        border-top-color: #27ae60;
    }

    .detail-group.mismatches {
        border-top-color: #e74c3c;
    }

    .detail-group h4 {
        color: #8b9dff;
        margin: 0 0 1.2em 0;
        text-transform: uppercase;
        font-size: 0.95em;
        letter-spacing: 1px;
    }

    .detail-item {
        background: rgba(0, 0, 0, 0.4);
        padding: 1em;
        border-radius: 8px;
        margin-bottom: 0.8em;
        display: flex;
        align-items: center;
        gap: 0.8em;
        border-left: 4px solid;
        transition: all 0.3s ease;
    }

    .detail-item:hover {
        background: rgba(0, 0, 0, 0.6);
        transform: translateX(4px);
    }

    .detail-item.match {
        border-left-color: #27ae60;
    }

    .detail-item.mismatch {
        border-left-color: #e74c3c;
    }

    .detail-icon {
        font-size: 1.5em;
        font-weight: bold;
    }

    .detail-text {
        flex: 1;
    }

    .detail-label {
        color: #8b9dff;
        font-weight: bold;
        font-size: 0.9em;
        margin-bottom: 0.2em;
    }

    .detail-value {
        color: #c0c0c0;
        font-size: 0.95em;
    }

    /* Action Buttons */
    .button-group {
        display: flex;
        gap: 1em;
        margin-top: 2em;
    }

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
        .compatibility-details {
            grid-template-columns: 1fr;
        }

        .stats-bar {
            grid-template-columns: 1fr;
        }

        .score-circle {
            width: 100px;
            height: 100px;
        }

        .score-number {
            font-size: 2em;
        }

        .comparison-table {
            padding: 1em;
        }

        th, td {
            padding: 0.8em;
            font-size: 0.9em;
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
        usernameCycleIndex: 0
    };

    async function initMatchmaking() {
        try {
            const userResponse = await fetch(`${pythonURI}/api/match/data`, {
                method: 'GET',
                credentials: 'include',
                headers: { 'Content-Type': 'application/json' }
            });

            if (!userResponse.ok) {
                throw new Error(`User profile error: ${userResponse.status}`);
            }

            const userData = await userResponse.json();
            if (!userData.data) {
                throw new Error('No profile data found');
            }
            state.currentUserProfile = userData.data;
            state.currentUserUID = userData.uid || 'current_user';

            const allResponse = await fetch(`${pythonURI}/api/match/all-data`, {
                method: 'GET',
                credentials: 'include',
                headers: { 'Content-Type': 'application/json' }
            });

            if (!allResponse.ok) {
                throw new Error(`Profiles error: ${allResponse.status}`);
            }

            const allData = await allResponse.json();
            
            if (!allData.users || !Array.isArray(allData.users)) {
                throw new Error('Invalid profile data format');
            }
            
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

    function calculateCompatibility(profile1, profile2) {
        const matches = [];
        const mismatches = [];
        let score = 0;

        const fields = ['age', 'location', 'interests', 'hobbies', 'occupation', 'bio', 'relationship_type', 'personality_type', 'mbti'];

        fields.forEach(field => {
            const val1 = profile1[field];
            const val2 = profile2[field];

            if (!val1 || !val2) return;

            const v1 = String(val1).toLowerCase().trim();
            const v2 = String(val2).toLowerCase().trim();

            if (v1 === v2) {
                matches.push({ field, value1: val1, value2: val2 });
                score += 20;
            } else if (field === 'age') {
                const age1 = parseInt(v1);
                const age2 = parseInt(v2);
                if (!isNaN(age1) && !isNaN(age2)) {
                    const diff = Math.abs(age1 - age2);
                    if (diff <= 3) {
                        matches.push({ field, value1: val1, value2: val2 });
                        score += 15;
                    } else if (diff <= 8) {
                        matches.push({ field, value1: val1, value2: val2 });
                        score += 8;
                    } else {
                        mismatches.push({ field, value1: val1, value2: val2 });
                    }
                }
            } else if (field === 'interests' || field === 'hobbies') {
                const arr1 = Array.isArray(val1) ? val1 : [val1];
                const arr2 = Array.isArray(val2) ? val2 : [val2];
                const commonCount = arr1.filter(i => arr2.some(j => 
                    String(i).toLowerCase() === String(j).toLowerCase()
                )).length;
                if (commonCount > 0) {
                    matches.push({ field, value1: commonCount, value2: `shared ${field}` });
                    score += commonCount * 10;
                } else {
                    mismatches.push({ field, value1: arr1[0], value2: arr2[0] });
                }
            } else {
                mismatches.push({ field, value1: val1, value2: val2 });
            }
        });

        const finalScore = Math.min(Math.round(score), 100);
        return { score: finalScore, matches, mismatches };
    }

    function buildComparisonTable(yourProfile, theirProfile) {
        // Debug logs to help identify backend structure
        console.log('yourProfile:', yourProfile);
        console.log('theirProfile:', theirProfile);
        // Username extraction: always 'You' for yourProfile, cycle through fixed list for theirProfile
        const username = 'You';
        const usernameCycle = [
            'indy', 'salem', 'phoenix', 'cody', 'pixel', 'cadence', 'ace', 'marco', 'libra', 'nikola', 'isaac', 'madam', 'flash', 'parker', 'merlin',
            'sky', 'toby', 'hop', 'niko', 'K9', 'thisisasupercooluser', 'Obama', 'JSN', 'Darnold', 'Walker', 'Mountbatten', 'Windsor'
        ];
        const theirusername = usernameCycle[state.usernameCycleIndex % usernameCycle.length];

    // Personality traits: only show decision, lifestyle, social
    const yourTraits = yourProfile?.profile?.profile_quiz?.analysis?.personalityTraits || {};
    const theirTraits = theirProfile?.profile?.profile_quiz?.analysis?.personalityTraits || {};
        let rows = '';
        // Username row
        rows += `
            <tr>
                <td class="attribute-name">Username</td>
                <td class="your-value">${formatValue(username)}</td>
                <td class="match-status username-match" style="color:#ffd700; font-size:1.5em;">~</td>
                <td class="their-value">${formatValue(theirusername)}</td>
            </tr>
        `;
        // Personality section title row
        rows += `
            <tr>
                <td colspan="4" style="text-align:center; font-weight:bold; color:#8b9dff; background:rgba(102,126,234,0.08);">Personality</td>
            </tr>
        `;
        // Only show decision, lifestyle, social
        const traitList = ['decision', 'lifestyle', 'social'];
        traitList.forEach(trait => {
            const yourVal = yourTraits[trait] !== undefined ? yourTraits[trait] : 'Not specified';
            const theirVal = theirTraits[trait] !== undefined ? theirTraits[trait] : 'Not specified';
            rows += `
                <tr>
                    <td class="attribute-name">${formatFieldName(trait)}</td>
                    <td class="your-value">${formatValue(yourVal)}</td>
                    <td class="match-status ${yourVal === theirVal ? 'match' : 'mismatch'}" style="font-size:1.5em;">
                        ${yourVal === theirVal ? '<span style="color:#27ae60;">✓</span>' : '<span style="color:#e74c3c;">✗</span>'}
                    </td>
                    <td class="their-value">${formatValue(theirVal)}</td>
                </tr>
            `;
        });
        return rows;
    }

    function showCurrentProfile() {
        if (state.currentIndex >= state.allProfiles.length) {
            showResults();
            return;
        }

        const profile = state.allProfiles[state.currentIndex];
        const tableRows = buildComparisonTable(state.currentUserProfile, profile.data);

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
                <button class="btn btn-skip" onclick="window.handleSkip()">
                    Skip
                </button>
                <button class="btn btn-match" onclick="window.handleMatch()">
                    Match
                </button>
            </div>
        `;
    }

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

    async function handleMatch() {
        const profile = state.allProfiles[state.currentIndex];
        const compatibility = calculateCompatibility(state.currentUserProfile, profile.data);
        
        state.matches.push({ ...profile, compatibility: compatibility.score });

        try {
            const existingMatches = state.currentUserProfile.matched_with || [];
            const updated = Array.isArray(existingMatches) ? existingMatches : [existingMatches];
            
            if (!updated.includes(profile.uid)) {
                updated.push(profile.uid);
            }

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
    window.handleSkip = handleSkip;

    function showResults() {
        const content = document.getElementById('mainContent');
        
        const reviewedText = state.allProfiles.length === 1 
            ? `You've reviewed the only available profile`
            : `You've completed reviewing all ${state.allProfiles.length} available profiles in the database`;
        
        const congratsMessage = state.matches.length > 0
            ? `Congratulations! You found <strong>${state.matches.length}</strong> potential connection${state.matches.length !== 1 ? 's' : ''}!`
            : `You've reached the end of all available profiles. No matches this round, but don't give up!`;
        
        content.innerHTML = `
            <div class="finish-screen">
                <h2>Matching Complete!</h2>
                <p style="color: #8b9dff; font-size: 1.2em; font-weight: 500; margin: 1.5em 0;">
                    ${reviewedText}
                </p>
                <p style="color: #27ae60; font-size: 1.3em; font-weight: bold; margin: 1.5em 0; padding: 1.5em; background: rgba(39, 174, 96, 0.1); border-radius: 8px; border: 2px solid #27ae60;">
                    ${congratsMessage}
                </p>

                <div class="stats-bar" style="margin: 2em 0; justify-content: center; display: flex; gap: 2em;">
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
                    <h3 style="color: #8b9dff; margin-top: 2em;">Your Matches</h3>
                    <div class="matches-grid">
                        ${state.matches.map(m => `
                            <div class="match-card">
                                <h4>${formatValue(m.data.name || m.uid)}</h4>
                                <p style="color: #c0c0c0; margin: 0.5em 0;">Somewhere on Earth</p>
                            </div>
                        `).join('')}
                    </div>
                ` : `
                    <div style="background: rgba(102, 126, 234, 0.1); padding: 2em; border-radius: 8px; margin-top: 2em; border: 2px dashed #667eea;">
                        <p style="color: #b0b0b0;">No matches this round. Try again to find your perfect match!</p>
                    </div>
                `}

                <div class="button-group" style="margin-top: 2em;">
                    <button class="btn btn-skip" onclick="location.reload()">
                        Start Over
                    </button>
                </div>
            </div>
        `;
    }

    function showNoProfiles() {
        const content = document.getElementById('mainContent');
        content.innerHTML = `
            <div class="error-message">
                <h3>No Profiles Available</h3>
                <p>Complete your profile first before matching with others!</p>
            </div>
        `;
    }

    function showError(message) {
        const content = document.getElementById('mainContent');
        content.innerHTML = `
            <div class="error-message">
                <h3>Error</h3>
                <p>${message}</p>
            </div>
        `;
    }

    initMatchmaking();

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
        if (!window.hasAccount) return false;
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

        navConnectors.forEach((conn, idx) => {
            if (visitedPages[idx + 1]) {
                conn.classList.add('visited');
            } else {
                conn.classList.remove('visited');
            }
        });

        const currentUrl = window.location.pathname;
        navNodes.forEach((node, idx) => {
            if (node.dataset.url === currentUrl) {
                node.classList.add('current');
            }
        });
    }

    visitedPages = loadVisitedPages();

    const currentUrl = window.location.pathname;
    pages.forEach((page, idx) => {
        if (page.url === currentUrl) {
            markPageVisited(page.id);
        }
    });

    updateNavigation();
</script>