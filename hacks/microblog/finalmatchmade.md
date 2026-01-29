---
layout: post
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
        max-width: 900px;
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
        font-size: 1.1em;
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

    .profile-section {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 2em;
        margin-bottom: 2em;
    }

    .profile-box {
        background: linear-gradient(135deg, #2a2a40 0%, #1f1f35 100%);
        border: 2px solid #667eea;
        border-radius: 10px;
        padding: 1.5em;
    }

    .profile-box h3 {
        color: #8b9dff;
        margin-top: 0;
        font-size: 1.3em;
        border-bottom: 2px solid #667eea;
        padding-bottom: 0.5em;
    }

    .profile-field {
        margin: 1em 0;
        padding: 0.8em;
        background: rgba(0, 0, 0, 0.3);
        border-radius: 6px;
        border-left: 3px solid #667eea;
    }

    .profile-field-label {
        color: #8b9dff;
        font-weight: bold;
        font-size: 0.9em;
        text-transform: uppercase;
        letter-spacing: 1px;
    }

    .profile-field-value {
        color: #e0e0e0;
        margin-top: 0.3em;
        font-size: 1.05em;
    }

    .compatibility-section {
        background: linear-gradient(135deg, #3a3a52 0%, #2d2d42 100%);
        border: 2px solid #667eea;
        border-radius: 10px;
        padding: 2em;
        margin-bottom: 2em;
    }

    .compatibility-score {
        text-align: center;
        margin-bottom: 2em;
    }

    .score-number {
        font-size: 4em;
        font-weight: bold;
        color: #667eea;
        margin: 0;
    }

    .score-label {
        color: #b0b0b0;
        font-size: 1.1em;
        margin: 0;
    }

    .compatibility-bar {
        width: 100%;
        height: 12px;
        background: #2a2a40;
        border-radius: 6px;
        overflow: hidden;
        margin-bottom: 2em;
    }

    .compatibility-fill {
        height: 100%;
        background: linear-gradient(90deg, #667eea, #8b9dff);
        transition: width 0.6s ease;
        border-radius: 6px;
    }

    .compatibility-details {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 1.5em;
    }

    .detail-group h4 {
        color: #8b9dff;
        margin: 0 0 1em 0;
        text-transform: uppercase;
        font-size: 0.95em;
        letter-spacing: 1px;
    }

    .detail-item {
        background: rgba(0, 0, 0, 0.3);
        padding: 1em;
        border-radius: 6px;
        margin-bottom: 0.8em;
        display: flex;
        align-items: center;
        gap: 0.8em;
        border-left: 4px solid;
    }

    .detail-item.match {
        border-left-color: #27ae60;
    }

    .detail-item.mismatch {
        border-left-color: #e74c3c;
    }

    .detail-icon {
        font-size: 1.5em;
    }

    .detail-text {
        flex: 1;
    }

    .detail-label {
        color: #8b9dff;
        font-weight: bold;
        font-size: 0.9em;
    }

    .detail-value {
        color: #c0c0c0;
        font-size: 0.95em;
        margin-top: 0.2em;
    }

    .button-group {
        display: flex;
        gap: 1em;
        margin-top: 2em;
    }

    .btn {
        flex: 1;
        padding: 1.2em;
        border: none;
        border-radius: 8px;
        font-size: 1.1em;
        font-weight: bold;
        cursor: pointer;
        transition: all 0.3s;
        text-transform: uppercase;
        letter-spacing: 1px;
    }

    .btn-match {
        background: linear-gradient(135deg, #27ae60, #229954);
        color: white;
    }

    .btn-match:hover:not(:disabled) {
        transform: translateY(-2px);
        box-shadow: 0 8px 20px rgba(39, 174, 96, 0.4);
    }

    .btn-skip {
        background: linear-gradient(135deg, #667eea, #5568d3);
        color: white;
    }

    .btn-skip:hover:not(:disabled) {
        transform: translateY(-2px);
        box-shadow: 0 8px 20px rgba(102, 126, 234, 0.4);
    }

    .btn:disabled {
        opacity: 0.5;
        cursor: not-allowed;
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
        border-radius: 8px;
        padding: 1.5em;
        text-align: center;
    }

    .stat-value {
        font-size: 2em;
        font-weight: bold;
        color: #8b9dff;
    }

    .stat-label {
        color: #b0b0b0;
        margin-top: 0.5em;
        font-size: 0.9em;
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
        grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
        gap: 1.5em;
        margin-top: 2em;
    }

    .match-card {
        background: linear-gradient(135deg, #2a2a40 0%, #1f1f35 100%);
        border: 2px solid #27ae60;
        border-radius: 10px;
        padding: 1.5em;
        transition: all 0.3s;
    }

    .match-card:hover {
        transform: translateY(-4px);
        box-shadow: 0 8px 25px rgba(39, 174, 96, 0.3);
    }

    .match-card h4 {
        color: #8b9dff;
        margin: 0 0 0.5em 0;
    }

    .match-card .compatibility-percent {
        color: #27ae60;
        font-weight: bold;
        font-size: 1.2em;
    }

    @media (max-width: 768px) {
        .profile-section {
            grid-template-columns: 1fr;
        }

        .compatibility-details {
            grid-template-columns: 1fr;
        }

        .stats-bar {
            grid-template-columns: 1fr;
        }
    }
</style>

<div class="matchmaking-container">
    <div class="header">
        <h1>Profile Matcher</h1>
        <p>Discover Compatible Connections</p>
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
        initialized: false
    };

    async function initMatchmaking() {
        try {
            // Get current user's profile
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
            state.currentUserProfile = userData.data;            state.currentUserUID = userData.uid || 'current_user';
            // Get all other profiles
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
            
            // Filter out current user and any empty profiles
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

        const fields = ['age', 'location', 'interests', 'hobbies', 'occupation', 'bio', 'relationship_type'];

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

        // Normalize score to 0-100
        const finalScore = Math.min(Math.round(score), 100);

        return { score: finalScore, matches, mismatches };
    }

    function showCurrentProfile() {
        if (state.currentIndex >= state.allProfiles.length) {
            showResults();
            return;
        }

        const profile = state.allProfiles[state.currentIndex];
        const compatibility = calculateCompatibility(state.currentUserProfile, profile.data);

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

            <div class="profile-section">
                <div class="profile-box">
                    <h3>👤 Your Profile</h3>
                    ${renderProfileFields(state.currentUserProfile)}
                </div>
                <div class="profile-box">
                    <h3>⭐ Their Profile</h3>
                    ${renderProfileFields(profile.data)}
                </div>
            </div>

            <div class="compatibility-section">
                <div class="compatibility-score">
                    <p class="score-number">${compatibility.score}%</p>
                    <p class="score-label">Compatibility Match</p>
                </div>
                <div class="compatibility-bar">
                    <div class="compatibility-fill" style="width: ${compatibility.score}%"></div>
                </div>

                <div class="compatibility-details">
                    <div class="detail-group">
                        <h4>✓ Compatibilities</h4>
                        ${compatibility.matches.length > 0 
                            ? compatibility.matches.map(m => `
                                <div class="detail-item match">
                                    <div class="detail-icon">✓</div>
                                    <div class="detail-text">
                                        <div class="detail-label">${formatFieldName(m.field)}</div>
                                        <div class="detail-value">${m.value1}</div>
                                    </div>
                                </div>
                            `).join('')
                            : '<p style="color: #b0b0b0;">No shared interests yet</p>'
                        }
                    </div>
                    <div class="detail-group">
                        <h4>✗ Differences</h4>
                        ${compatibility.mismatches.length > 0 
                            ? compatibility.mismatches.map(m => `
                                <div class="detail-item mismatch">
                                    <div class="detail-icon">→</div>
                                    <div class="detail-text">
                                        <div class="detail-label">${formatFieldName(m.field)}</div>
                                        <div class="detail-value">You: ${m.value1} / They: ${m.value2}</div>
                                    </div>
                                </div>
                            `).join('')
                            : '<p style="color: #b0b0b0;">Great match all around!</p>'
                        }
                    </div>
                </div>
            </div>

            <div class="button-group">
                <button class="btn btn-skip" onclick="handleSkip()">
                    ➜ Skip
                </button>
                <button class="btn btn-match" onclick="handleMatch()">
                    Match
                </button>
            </div>
        `;
    }

    function renderProfileFields(profile) {
        if (!profile) return '<p style="color: #b0b0b0;">No data available</p>';

        return Object.entries(profile)
            .filter(([key]) => key !== 'id' && key !== 'uid')
            .map(([key, value]) => `
                <div class="profile-field">
                    <div class="profile-field-label">${formatFieldName(key)}</div>
                    <div class="profile-field-value">${formatValue(value)}</div>
                </div>
            `).join('');
    }

    function formatFieldName(field) {
        return field.replace(/_/g, ' ').replace(/\b\w/g, l => l.toUpperCase());
    }

    function formatValue(value) {
        if (Array.isArray(value)) return value.join(', ');
        return value || 'Not specified';
    }

    async function handleMatch() {
        const profile = state.allProfiles[state.currentIndex];
        const compatibility = calculateCompatibility(state.currentUserProfile, profile.data);
        
        state.matches.push({ ...profile, compatibility: compatibility.score });

        // Save to backend
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
        showCurrentProfile();
    }

    function handleSkip() {
        state.skipped.push(state.allProfiles[state.currentIndex]);
        state.currentIndex++;
        showCurrentProfile();
    }

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
                <h2>🎉 Matching Complete!</h2>
                <p style="color: #8b9dff; font-size: 1.2em; font-weight: 500; margin: 1.5em 0;">
                    ${reviewedText}
                </p>
                <p style="color: #27ae60; font-size: 1.3em; font-weight: bold; margin: 1.5em 0; padding: 1.5em; background: rgba(39, 174, 96, 0.1); border-radius: 8px; border: 2px solid #27ae60;">
                    ${congratsMessage}
                </p>

                <div class="stats-bar" style="margin: 2em 0;">
                    <div class="stat-box">
                        <div class="stat-value">${state.matches.length}</div>
                        <div class="stat-label">Total Matches</div>
                    </div>
                    <div class="stat-box">
                        <div class="stat-value">${state.skipped.length}</div>
                        <div class="stat-label">Skipped</div>
                    </div>
                    <div class="stat-box">
                        <div class="stat-value">${state.matches.length > 0 ? Math.round(state.matches.reduce((sum, m) => sum + m.compatibility, 0) / state.matches.length) : 0}%</div>
                        <div class="stat-label">Avg Compatibility</div>
                    </div>
                </div>

                ${state.matches.length > 0 ? `
                    <h3 style="color: #8b9dff; margin-top: 2em;">Your Matches</h3>
                    <div class="matches-grid">
                        ${state.matches.map(m => `
                            <div class="match-card">
                                <h4>${formatValue(m.data.name || m.uid)}</h4>
                                <p style="color: #c0c0c0; margin: 0.5em 0;">${formatValue(m.data.location || 'Location unknown')}</p>
                                <div class="compatibility-percent">Match: ${m.compatibility}%</div>
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
                        ↻ Start Over
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
                <h3>⚠️ Error</h3>
                <p>${message}</p>
            </div>
        `;
    }

    // Initialize on load
    initMatchmaking();
</script>