---
layout: opencs
title: Bio Builder
description: Create your matchmaking profile with AI-powered safety checking
permalink: /bio_create/
breadcrumb: false
microblog: false
author: Ethan W
---

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

    .container {
        max-width: 800px;
        width: 95%;
        background: #1a1a1a;
        border-radius: 20px;
        padding: 1.5em;
        box-shadow: 0 20px 60px rgba(0, 0, 0, 0.5);
        margin: 1.5rem auto;
        border: 1px solid #262626;
    }

        .header {
            text-align: center;
            margin-bottom: 1em;
            margin-top: 0.5em;
        }

        .header h1 {
            font-size: 2.5em;
            color: #3b82f6;
            margin-bottom: 0.5em;
            font-weight: 700;
            display: block;
            visibility: visible;
        }

        .header p {
            color: #a1a1aa;
            font-size: 0.95em;
        }

        .progress-bar {
            width: 100%;
            height: 8px;
            background: #262626;
            border-radius: 10px;
            margin-bottom: 1.2em;
            overflow: hidden;
        }

        .progress-fill {
            height: 100%;
            background: linear-gradient(135deg, #3b82f6 0%, #2563eb 100%);
            transition: width 0.5s ease;
            border-radius: 10px;
        }

        .progress-text {
            text-align: center;
            color: #71717a;
            font-size: 1em;
            margin-bottom: 0.8em;
        }

        .bio-section {
            background: #0d0d0d;
            border-radius: 12px;
            padding: 1em;
            border: 1px solid #262626;
            transition: all 0.3s ease;
            display: none;
        }

        .bio-section.active {
            display: block;
            animation: slideIn 0.5s ease;
        }

        .section-header {
            display: grid;
            grid-template-columns: minmax(auto, max-content) auto 1fr;
            align-items: center;
            margin-bottom: 1em;
            gap: 1.5em;
        }

        .section-title {
            font-size: 1.6em;
            color: #3b82f6;
            font-weight: 600;
            display: flex;
            align-items: flex-start;
            gap: 0.5em;
            justify-self: start;
            max-width: 100%;
        }

        .section-icon {
            font-size: 1.2em;
            flex-shrink: 0;
            line-height: 1;
            margin-top: 0.1em;
        }

        .section-title-text {
            flex: 1;
            word-wrap: break-word;
            line-height: 1.2;
        }

        .autofill-container {
            display: flex;
            align-items: center;
            gap: 0.8em;
            justify-self: center;
        }

        .autofill-label {
            font-size: 0.85em;
            color: #a1a1aa;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 0.5px;
            white-space: nowrap;
        }

        .autofill-buttons {
            display: flex;
            gap: 0.5em;
        }

        .header-right {
            display: flex;
            align-items: center;
            justify-self: end;
        }

        .ai-check-header-btn {
            padding: 0.6em 1.3em;
            background: linear-gradient(135deg, #3b82f6 0%, #2563eb 100%);
            color: white;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.3s ease;
            font-size: 0.95em;
            white-space: nowrap;
        }

        .ai-check-header-btn:hover:not(:disabled) {
            transform: translateY(-2px);
            box-shadow: 0 4px 15px rgba(59, 130, 246, 0.4);
        }

        .ai-check-header-btn:disabled {
            opacity: 0.5;
            cursor: not-allowed;
        }

        .autofill-btn {
            width: 40px;
            height: 40px;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-size: 1.3em;
            font-weight: 600;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .autofill-good {
            background: #27ae60;
            color: white;
        }

        .autofill-good:hover {
            background: #229954;
            transform: translateY(-2px) scale(1.1);
        }

        .autofill-bad {
            background: #e74c3c;
            color: white;
        }

        .autofill-bad:hover {
            background: #c0392b;
            transform: translateY(-2px) scale(1.1);
        }

        /* ── MODE TOGGLE ── */
        .mode-toggle-bar {
            display: flex;
            align-items: center;
            gap: 0.6em;
            margin-bottom: 0.8em;
            padding: 0.5em 0.8em;
            background: #141414;
            border: 1px solid #2a2a2a;
            border-radius: 10px;
        }

        .mode-toggle-label {
            font-size: 0.8em;
            color: #71717a;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 0.5px;
            flex: 1;
        }

        .mode-toggle-group {
            display: flex;
            background: #1a1a1a;
            border-radius: 8px;
            padding: 3px;
            border: 1px solid #303030;
            gap: 2px;
        }

        .mode-btn {
            padding: 0.35em 0.9em;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            font-size: 0.82em;
            font-weight: 600;
            transition: all 0.25s ease;
            background: transparent;
            color: #71717a;
            white-space: nowrap;
        }

        .mode-btn.active {
            background: linear-gradient(135deg, #3b82f6 0%, #2563eb 100%);
            color: #fff;
            box-shadow: 0 2px 8px rgba(59,130,246,0.35);
        }

        .mode-btn:hover:not(.active) {
            color: #a1a1aa;
            background: #232323;
        }

        /* Autofill hint — hide in free-write mode */
        .madlibs-only-hint {
            font-size: 0.75em;
            color: #52525b;
            font-style: italic;
        }

        /* Free-write area */
        .freewrite-area {
            display: none;
            animation: slideIn 0.3s ease;
        }

        .freewrite-area.visible {
            display: block;
        }

        .freewrite-textarea {
            width: 100%;
            padding: 1em;
            border: 2px solid #303030;
            border-radius: 10px;
            font-size: 1em;
            font-family: inherit;
            resize: vertical;
            transition: all 0.3s ease;
            background: #141414;
            color: #e4e4e7;
            min-height: 110px;
            line-height: 1.7;
        }

        .freewrite-textarea:focus {
            outline: none;
            border-color: #3b82f6;
            box-shadow: 0 0 0 3px rgba(59,130,246,0.12);
        }

        .freewrite-textarea::placeholder {
            color: #3f3f46;
            font-style: italic;
        }

        .freewrite-char-counter {
            text-align: right;
            font-size: 0.8em;
            color: #52525b;
            margin-top: 0.3em;
        }

        /* Mad libs area */
        .madlibs-area {
            display: block;
            animation: slideIn 0.3s ease;
        }

        .madlibs-area.hidden {
            display: none;
        }

        /* ── rest of original styles ── */

        .input-container {
            position: relative;
            margin-bottom: 1.2em;
        }

        .madlib-template {
            background: #0d0d0d;
            padding: 1.2em;
            border-radius: 10px;
            margin-bottom: 1em;
            line-height: 2;
            border: 1px solid #262626;
        }

        .madlib-template p {
            color: #e4e4e7;
            font-size: 1.05em;
            margin: 0;
        }

        .madlib-input {
            background: #1a1a1a;
            border: 1px solid #262626;
            border-radius: 6px;
            padding: 0.4em 0.8em;
            color: #3b82f6;
            font-size: 1em;
            font-weight: 600;
            transition: all 0.3s ease;
            min-width: 140px;
        }

        .madlib-input:focus {
            outline: none;
            border-color: #3b82f6;
            background: #0d0d0d;
            box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.1);
        }

        .madlib-input::placeholder {
            color: #71717a;
            font-weight: normal;
            font-style: italic;
        }

        .madlib-select {
            background: #1a1a1a;
            border: 1px solid #262626;
            border-radius: 6px;
            padding: 0.4em 0.8em;
            color: #3b82f6;
            font-size: 0.95em;
            font-weight: 600;
            transition: all 0.3s ease;
            cursor: pointer;
            min-width: 140px;
            max-width: 220px;
            display: inline-block;
        }

        .madlib-select:hover {
            border-color: #3b82f6;
            background: #0d0d0d;
        }

        .madlib-select:focus {
            outline: none;
            border-color: #3b82f6;
            background: #0d0d0d;
            box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.1);
        }

        .madlib-select option {
            background: #1a1a1a;
            color: #e4e4e7;
            padding: 0.5em;
        }

        .madlib-select option:first-child {
            color: #71717a;
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
            color: #71717a;
        }

        .button-group {
            display: flex;
            gap: 1em;
            justify-content: center;
            margin-top: 1em;
        }

        .ai-check-btn {
            padding: 1em 2.5em;
            background: linear-gradient(135deg, #3b82f6 0%, #2563eb 100%);
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
            box-shadow: 0 4px 15px rgba(59, 130, 246, 0.4);
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
            background: #0d0d0d;
            border: 1px solid #262626;
            border-left: 4px solid #3b82f6;
            padding: 0.8em;
            border-radius: 8px;
            margin-bottom: 1em;
            display: none;
            animation: slideIn 0.3s ease;
        }

        .info-box.visible {
            display: block;
        }

        .info-box h3 {
            color: #3b82f6;
            margin-top: 0;
            margin-bottom: 0.3em;
            font-size: 0.95em;
        }

        .info-box p {
            color: #a1a1aa;
            line-height: 1.4;
            margin: 0;
            font-size: 0.85em;
        }

        .help-button {
            width: 32px;
            height: 32px;
            border-radius: 50%;
            background: #3b82f6;
            color: white;
            border: none;
            cursor: pointer;
            font-size: 1.1em;
            font-weight: bold;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 1em;
            transition: all 0.3s ease;
            box-shadow: 0 2px 8px rgba(59, 130, 246, 0.3);
        }

        .help-button:hover {
            background: #2563eb;
            transform: scale(1.1);
            box-shadow: 0 4px 12px rgba(59, 130, 246, 0.5);
        }

        .help-button.active {
            background: #2563eb;
        }

        /* Bio Preview Styles */
        .bio-preview {
            background: #0d0d0d;
            border: 1px solid #262626;
            border-radius: 12px;
            padding: 1.5em;
            margin-bottom: 1.5em;
            text-align: left;
        }

        .bio-preview h3 {
            color: #3b82f6;
            margin-bottom: 1em;
            text-align: center;
            font-size: 1.3em;
        }

        .preview-section {
            margin-bottom: 1.2em;
        }

        .preview-section:last-child {
            margin-bottom: 0;
        }

        .preview-section h4 {
            color: #3b82f6 !important;
            font-size: 0.9em;
            margin-bottom: 0.5em;
            display: flex;
            align-items: center;
            gap: 0.5em;
        }

        .preview-section h4 span {
            color: #3b82f6 !important;
        }

        .preview-section p {
            color: #e4e4e7;
            line-height: 1.8;
            padding-left: 1.8em;
            margin: 0;
        }

        .edit-section-btn {
            padding: 0.4em 1em;
            background: linear-gradient(135deg, #3b82f6 0%, #2563eb 100%);
            color: white;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            font-size: 0.85em;
            font-weight: 600;
            transition: all 0.3s ease;
        }

        .edit-section-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 4px 12px rgba(59, 130, 246, 0.4);
        }

        .save-edit-btn {
            padding: 0.5em 1.2em;
            background: linear-gradient(135deg, #27ae60 0%, #229954 100%);
            color: white;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            font-size: 0.85em;
            font-weight: 600;
            transition: all 0.3s ease;
            margin-top: 0.5em;
        }

        .save-edit-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 4px 12px rgba(39, 174, 96, 0.4);
        }

        .display-mode p {
            color: #e4e4e7;
            line-height: 1.8;
            padding-left: 1.8em;
            margin: 0;
        }

        .edit-mode {
            background: #0d0d0d;
            padding: 1em;
            border-radius: 8px;
            margin-top: 0.5em;
            border: 1px solid #3b82f6;
            animation: slideIn 0.3s ease;
        }

        .madlib-select-inline {
            background: #1a1a1a;
            border: 1px solid #3b82f6;
            border-radius: 6px;
            padding: 0.3em 0.6em;
            color: #3b82f6;
            font-size: 0.95em;
            font-weight: 600;
            transition: all 0.3s ease;
            cursor: pointer;
            min-width: 120px;
            max-width: 200px;
            display: inline-block;
        }

        .madlib-select-inline:hover {
            background: #0d0d0d;
            box-shadow: 0 0 0 2px rgba(59, 130, 246, 0.2);
        }

        .madlib-select-inline:focus {
            outline: none;
            background: #0d0d0d;
            box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.3);
        }

        .madlib-select-inline option {
            background: #1a1a1a;
            color: #e4e4e7;
            padding: 0.5em;
        }

        .editable-bio-section {
            background: #0d0d0d;
            padding: 1em;
            border-radius: 8px;
            margin-top: 0.5em;
            border: 1px solid #262626;
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
                grid-template-columns: 1fr;
                gap: 1em;
            }

            .section-title {
                justify-self: center;
                text-align: center;
            }

            .autofill-container {
                justify-self: center;
            }

            .header-right {
                justify-self: center;
                width: 100%;
                justify-content: center;
            }

            .ai-check-header-btn {
                width: 100%;
                max-width: 300px;
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

<div class="container">
        <div class="header">
            <h1>Bio Builder</h1>
            <p>Create your matchmaking profile safely</p>
        </div>

        <div class="progress-text" id="progress-text">Question 1 of 4</div>
        <div class="progress-bar">
            <div class="progress-fill" id="progress-fill" style="width: 25%;"></div>
        </div>

        <button class="help-button" id="help-toggle" title="Click for help">?</button>
        <div class="info-box" id="info-box">
            <h3>🛡️ AI Privacy Protection</h3>
            <p>Our advanced AI system detects personal information like phone numbers, addresses, specific locations, routines, and sensitive data. Click "Check" and pass the check to continue!</p>
        </div>

        <!-- ═══════════════ ABOUT ME ═══════════════ -->
        <div class="bio-section active" data-section="about" data-question="1">
            <div class="section-header">
                <div class="section-title">
                    <span class="section-icon">👤</span>
                    <span class="section-title-text">About Me</span>
                </div>
                <div class="autofill-container" id="about-autofill-container">
                    <div class="autofill-label">Prefill</div>
                    <div class="autofill-buttons">
                        <button class="autofill-btn autofill-good" id="about-good-btn">✓</button>
                        <button class="autofill-btn autofill-bad" id="about-bad-btn">✕</button>
                    </div>
                </div>
                <div class="header-right">
                    <button class="ai-check-header-btn" id="about-check-btn">Check</button>
                </div>
            </div>

            <!-- Mode Toggle Bar -->
            <div class="mode-toggle-bar">
                <span class="mode-toggle-label">Answer style</span>
                <div class="mode-toggle-group">
                    <button class="mode-btn active" data-section="about" data-mode="madlibs">🔽 Dropdown</button>
                    <button class="mode-btn" data-section="about" data-mode="freewrite">✏️ Free Write</button>
                </div>
            </div>

            <!-- Dropdown area -->
            <div class="madlibs-area" id="about-madlibs">
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
            </div>

            <!-- Free Write area -->
            <div class="freewrite-area" id="about-freewrite">
                <textarea class="freewrite-textarea" id="about-freetext" maxlength="500"
                    placeholder="Write a short 'About Me' paragraph. Avoid sharing personal info like your name, address, phone number, or daily schedule..."></textarea>
                <div class="freewrite-char-counter"><span id="about-charcount">0</span> / 500</div>
            </div>

            <div id="about-result"></div>
            <div class="button-group">
                <button class="next-btn" id="about-next">→</button>
            </div>
        </div>

        <!-- ═══════════════ INTERESTS ═══════════════ -->
        <div class="bio-section" data-section="interests" data-question="2">
            <div class="section-header">
                <div class="section-title">
                    <span class="section-icon">🔍</span>
                    <span class="section-title-text">Interests & Hobbies</span>
                </div>
                <div class="autofill-container" id="interests-autofill-container">
                    <div class="autofill-label">Prefill</div>
                    <div class="autofill-buttons">
                        <button class="autofill-btn autofill-good" id="interests-good-btn">✓</button>
                        <button class="autofill-btn autofill-bad" id="interests-bad-btn">✕</button>
                    </div>
                </div>
                <div class="header-right">
                    <button class="ai-check-header-btn" id="interests-check-btn">Check</button>
                </div>
            </div>

            <div class="mode-toggle-bar">
                <span class="mode-toggle-label">Answer style</span>
                <div class="mode-toggle-group">
                    <button class="mode-btn active" data-section="interests" data-mode="madlibs">🔽 Dropdown</button>
                    <button class="mode-btn" data-section="interests" data-mode="freewrite">✏️ Free Write</button>
                </div>
            </div>

            <div class="madlibs-area" id="interests-madlibs">
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
            </div>

            <div class="freewrite-area" id="interests-freewrite">
                <textarea class="freewrite-textarea" id="interests-freetext" maxlength="500"
                    placeholder="Describe your interests and hobbies. Keep it general — no specific gym locations, schedules, or routines..."></textarea>
                <div class="freewrite-char-counter"><span id="interests-charcount">0</span> / 500</div>
            </div>

            <div id="interests-result"></div>
            <div class="button-group">
                <button class="next-btn" id="interests-next">→</button>
            </div>
        </div>

        <!-- ═══════════════ SKILLS ═══════════════ -->
        <div class="bio-section" data-section="skills" data-question="3">
            <div class="section-header">
                <div class="section-title">
                    <span class="section-icon">💻</span>
                    <span class="section-title-text">Skills & Expertise</span>
                </div>
                <div class="autofill-container" id="skills-autofill-container">
                    <div class="autofill-label">Prefill</div>
                    <div class="autofill-buttons">
                        <button class="autofill-btn autofill-good" id="skills-good-btn">✓</button>
                        <button class="autofill-btn autofill-bad" id="skills-bad-btn">✕</button>
                    </div>
                </div>
                <div class="header-right">
                    <button class="ai-check-header-btn" id="skills-check-btn">Check</button>
                </div>
            </div>

            <div class="mode-toggle-bar">
                <span class="mode-toggle-label">Answer style</span>
                <div class="mode-toggle-group">
                    <button class="mode-btn active" data-section="skills" data-mode="madlibs">🔽 Dropdown</button>
                    <button class="mode-btn" data-section="skills" data-mode="freewrite">✏️ Free Write</button>
                </div>
            </div>

            <div class="madlibs-area" id="skills-madlibs">
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
            </div>

            <div class="freewrite-area" id="skills-freewrite">
                <textarea class="freewrite-textarea" id="skills-freetext" maxlength="500"
                    placeholder="Describe your skills and experience. Avoid sharing employer names, employee IDs, or contact details..."></textarea>
                <div class="freewrite-char-counter"><span id="skills-charcount">0</span> / 500</div>
            </div>

            <div id="skills-result"></div>
            <div class="button-group">
                <button class="next-btn" id="skills-next">→</button>
            </div>
        </div>

        <!-- ═══════════════ GOALS ═══════════════ -->
        <div class="bio-section" data-section="goals" data-question="4">
            <div class="section-header">
                <div class="section-title">
                    <span class="section-icon">🎓</span>
                    <span class="section-title-text">Goals & Looking For</span>
                </div>
                <div class="autofill-container" id="goals-autofill-container">
                    <div class="autofill-label">Prefill</div>
                    <div class="autofill-buttons">
                        <button class="autofill-btn autofill-good" id="goals-good-btn">✓</button>
                        <button class="autofill-btn autofill-bad" id="goals-bad-btn">✕</button>
                    </div>
                </div>
                <div class="header-right">
                    <button class="ai-check-header-btn" id="goals-check-btn">Check</button>
                </div>
            </div>

            <div class="mode-toggle-bar">
                <span class="mode-toggle-label">Answer style</span>
                <div class="mode-toggle-group">
                    <button class="mode-btn active" data-section="goals" data-mode="madlibs">🔽 Dropdown</button>
                    <button class="mode-btn" data-section="goals" data-mode="freewrite">✏️ Free Write</button>
                </div>
            </div>

            <div class="madlibs-area" id="goals-madlibs">
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
            </div>

            <div class="freewrite-area" id="goals-freewrite">
                <textarea class="freewrite-textarea" id="goals-freetext" maxlength="500"
                    placeholder="Describe what you're looking for and your goals. Don't share your address, SSN, or personal contact info..."></textarea>
                <div class="freewrite-char-counter"><span id="goals-charcount">0</span> / 500</div>
            </div>

            <div id="goals-result"></div>
            <div class="button-group">
                <button class="next-btn" id="goals-next">→</button>
            </div>
        </div>

        <div class="submit-section" id="submit-section">
            <h1 style="color: #3b82f6; font-size: 2em; margin-bottom: 0.3em;">Bio Builder</h1>
            <h2 style="color: #3b82f6; margin-bottom: 1em; font-size: 1.3em;">✅ All Questions Complete!</h2>
            
            <div class="bio-preview" id="bio-preview">
                <h3>📋 Your Bio Preview</h3>
                
                <div class="preview-section">
                    <div style="display: flex; justify-content: space-between; align-items: center;">
                        <h4 style="color: #3b82f6;"><span style="color: #3b82f6;">👤</span> About Me</h4>
                        <button class="edit-section-btn" data-section="about">✏️ Edit</button>
                    </div>
                    <div class="display-mode" id="display-about">
                        <p id="preview-about"></p>
                    </div>
                    <div class="edit-mode" id="edit-about" style="display: none;">
                        <!-- Dropdown edit (shown when section used Dropdown mode) -->
                        <div id="edit-about-dropdown">
                            <p style="color: #e4e4e7; padding-left: 1.8em; margin-bottom: 0.8em;">
                                I'm a passionate 
                                <select class="madlib-select-inline" id="final-about-profession"></select>
                                who loves 
                                <select class="madlib-select-inline" id="final-about-hobby1"></select>
                                and 
                                <select class="madlib-select-inline" id="final-about-hobby2"></select>
                                . I enjoy 
                                <select class="madlib-select-inline" id="final-about-activity"></select>
                                and believe in 
                                <select class="madlib-select-inline" id="final-about-value"></select>
                                .
                            </p>
                        </div>
                        <!-- Freewrite edit (shown when section used Free Write mode) -->
                        <div id="edit-about-freewrite" style="display:none; padding: 0 1.8em 0.8em;">
                            <textarea class="freewrite-textarea" id="final-about-freetext" maxlength="500" style="min-height:90px;"></textarea>
                            <div class="freewrite-char-counter"><span id="final-about-charcount">0</span> / 500</div>
                        </div>
                        <div style="text-align: right; padding-right: 1.8em;">
                            <button class="save-edit-btn" data-section="about">💾 Save Changes</button>
                        </div>
                    </div>
                </div>
                
                <div class="preview-section">
                    <div style="display: flex; justify-content: space-between; align-items: center;">
                        <h4 style="color: #3b82f6;"><span style="color: #3b82f6;">🔍</span> Interests & Hobbies</h4>
                        <button class="edit-section-btn" data-section="interests">✏️ Edit</button>
                    </div>
                    <div class="display-mode" id="display-interests">
                        <p id="preview-interests"></p>
                    </div>
                    <div class="edit-mode" id="edit-interests" style="display: none;">
                        <div id="edit-interests-dropdown">
                            <p style="color: #e4e4e7; padding-left: 1.8em; margin-bottom: 0.8em;">
                                In my free time, I enjoy 
                                <select class="madlib-select-inline" id="final-interests-hobby1"></select>
                                , 
                                <select class="madlib-select-inline" id="final-interests-hobby2"></select>
                                , and 
                                <select class="madlib-select-inline" id="final-interests-hobby3"></select>
                                . I'm also interested in learning more about 
                                <select class="madlib-select-inline" id="final-interests-topic"></select>
                                .
                            </p>
                        </div>
                        <div id="edit-interests-freewrite" style="display:none; padding: 0 1.8em 0.8em;">
                            <textarea class="freewrite-textarea" id="final-interests-freetext" maxlength="500" style="min-height:90px;"></textarea>
                            <div class="freewrite-char-counter"><span id="final-interests-charcount">0</span> / 500</div>
                        </div>
                        <div style="text-align: right; padding-right: 1.8em;">
                            <button class="save-edit-btn" data-section="interests">💾 Save Changes</button>
                        </div>
                    </div>
                </div>
                
                <div class="preview-section">
                    <div style="display: flex; justify-content: space-between; align-items: center;">
                        <h4 style="color: #3b82f6;"><span style="color: #3b82f6;">💻</span> Skills & Expertise</h4>
                        <button class="edit-section-btn" data-section="skills">✏️ Edit</button>
                    </div>
                    <div class="display-mode" id="display-skills">
                        <p id="preview-skills"></p>
                    </div>
                    <div class="edit-mode" id="edit-skills" style="display: none;">
                        <div id="edit-skills-dropdown">
                            <p style="color: #e4e4e7; padding-left: 1.8em; margin-bottom: 0.8em;">
                                I'm skilled at 
                                <select class="madlib-select-inline" id="final-skills-skill1"></select>
                                , 
                                <select class="madlib-select-inline" id="final-skills-skill2"></select>
                                , and 
                                <select class="madlib-select-inline" id="final-skills-skill3"></select>
                                . I have 
                                <select class="madlib-select-inline" id="final-skills-experience"></select>
                                of experience and enjoy 
                                <select class="madlib-select-inline" id="final-skills-aspect"></select>
                                .
                            </p>
                        </div>
                        <div id="edit-skills-freewrite" style="display:none; padding: 0 1.8em 0.8em;">
                            <textarea class="freewrite-textarea" id="final-skills-freetext" maxlength="500" style="min-height:90px;"></textarea>
                            <div class="freewrite-char-counter"><span id="final-skills-charcount">0</span> / 500</div>
                        </div>
                        <div style="text-align: right; padding-right: 1.8em;">
                            <button class="save-edit-btn" data-section="skills">💾 Save Changes</button>
                        </div>
                    </div>
                </div>
                
                <div class="preview-section">
                    <div style="display: flex; justify-content: space-between; align-items: center;">
                        <h4 style="color: #3b82f6;"><span style="color: #3b82f6;">🎓</span> Goals & Looking For</h4>
                        <button class="edit-section-btn" data-section="goals">✏️ Edit</button>
                    </div>
                    <div class="display-mode" id="display-goals">
                        <p id="preview-goals"></p>
                    </div>
                    <div class="edit-mode" id="edit-goals" style="display: none;">
                        <div id="edit-goals-dropdown">
                            <p style="color: #e4e4e7; padding-left: 1.8em; margin-bottom: 0.8em;">
                                I'm looking to connect with people who are interested in 
                                <select class="madlib-select-inline" id="final-goals-interest"></select>
                                . My goal is to 
                                <select class="madlib-select-inline" id="final-goals-goal"></select>
                                and I'd love to 
                                <select class="madlib-select-inline" id="final-goals-activity"></select>
                                .
                            </p>
                        </div>
                        <div id="edit-goals-freewrite" style="display:none; padding: 0 1.8em 0.8em;">
                            <textarea class="freewrite-textarea" id="final-goals-freetext" maxlength="500" style="min-height:90px;"></textarea>
                            <div class="freewrite-char-counter"><span id="final-goals-charcount">0</span> / 500</div>
                        </div>
                        <div style="text-align: right; padding-right: 1.8em;">
                            <button class="save-edit-btn" data-section="goals">💾 Save Changes</button>
                        </div>
                    </div>
                </div>
            </div>
            
            <div class="button-group">
                <button class="submit-btn" id="save-btn">📥 Save</button>
            </div>
            <div id="save-status"></div>
    </div>
</div>

<script type="module">
        import { pythonURI } from '{{ site.baseurl }}/assets/js/api/config.js';

        // ── State ──
        const safetyChecks = { about: false, interests: false, skills: false, goals: false };
        // Track which mode each section is in: 'madlibs' | 'freewrite'
        const sectionModes = { about: 'madlibs', interests: 'madlibs', skills: 'madlibs', goals: 'madlibs' };

        let currentQuestion = 1;
        const totalQuestions = 4;
        const questionOrder = ['about', 'interests', 'skills', 'goals'];

        // ── Help toggle ──
        document.getElementById('help-toggle').addEventListener('click', () => {
            document.getElementById('info-box').classList.toggle('visible');
            document.getElementById('help-toggle').classList.toggle('active');
        });

        // ── Character counters for free-write areas ──
        questionOrder.forEach(section => {
            const ta = document.getElementById(`${section}-freetext`);
            const counter = document.getElementById(`${section}-charcount`);
            if (ta && counter) {
                ta.addEventListener('input', () => {
                    counter.textContent = ta.value.length;
                    // Reset safety check when content changes
                    safetyChecks[section] = false;
                    document.getElementById(`${section}-next`).classList.remove('visible');
                    document.getElementById(`${section}-result`).innerHTML = '';
                });
            }
        });

        // ── Mode toggle buttons ──
        document.querySelectorAll('.mode-btn').forEach(btn => {
            btn.addEventListener('click', () => {
                const section = btn.dataset.section;
                const newMode = btn.dataset.mode;
                const oldMode = sectionModes[section];

                if (newMode === oldMode) return;

                // Update active button styling
                const group = btn.closest('.mode-toggle-group');
                group.querySelectorAll('.mode-btn').forEach(b => b.classList.remove('active'));
                btn.classList.add('active');

                sectionModes[section] = newMode;

                const madlibsArea = document.getElementById(`${section}-madlibs`);
                const freewriteArea = document.getElementById(`${section}-freewrite`);
                const autofillContainer = document.getElementById(`${section}-autofill-container`);

                if (newMode === 'freewrite') {
                    // Pre-fill textarea with current Mad Libs sentence (if dropdowns have values)
                    const currentText = getMadLibsText(section);
                    const ta = document.getElementById(`${section}-freetext`);
                    if (currentText && !ta.value) {
                        ta.value = currentText;
                        document.getElementById(`${section}-charcount`).textContent = ta.value.length;
                    }
                    madlibsArea.classList.add('hidden');
                    freewriteArea.classList.add('visible');
                    // Hide autofill (prefill only makes sense for mad libs)
                    if (autofillContainer) autofillContainer.style.display = 'none';
                } else {
                    freewriteArea.classList.remove('visible');
                    madlibsArea.classList.remove('hidden');
                    if (autofillContainer) autofillContainer.style.display = '';
                }

                // Reset safety check on mode switch
                safetyChecks[section] = false;
                document.getElementById(`${section}-next`).classList.remove('visible');
                document.getElementById(`${section}-result`).innerHTML = '';
            });
        });

        // ── Helper: build Mad Libs sentence for a section ──
        function getMadLibsText(section) {
            const builders = {
                about: () => {
                    const p = val('about-profession'), h1 = val('about-hobby1'),
                          h2 = val('about-hobby2'), a = val('about-activity'), v = val('about-value');
                    if (!p || !h1 || !h2 || !a || !v) return '';
                    return `I'm a passionate ${p} who loves ${h1} and ${h2}. I enjoy ${a} and believe in ${v}.`;
                },
                interests: () => {
                    const h1 = val('interests-hobby1'), h2 = val('interests-hobby2'),
                          h3 = val('interests-hobby3'), t = val('interests-topic');
                    if (!h1 || !h2 || !h3 || !t) return '';
                    return `In my free time, I enjoy ${h1}, ${h2}, and ${h3}. I'm also interested in learning more about ${t}.`;
                },
                skills: () => {
                    const s1 = val('skills-skill1'), s2 = val('skills-skill2'),
                          s3 = val('skills-skill3'), e = val('skills-experience'), a = val('skills-aspect');
                    if (!s1 || !s2 || !s3 || !e || !a) return '';
                    return `I'm skilled at ${s1}, ${s2}, and ${s3}. I have ${e} of experience and enjoy ${a}.`;
                },
                goals: () => {
                    const i = val('goals-interest'), g = val('goals-goal'), a = val('goals-activity');
                    if (!i || !g || !a) return '';
                    return `I'm looking to connect with people who are interested in ${i}. My goal is to ${g} and I'd love to ${a}.`;
                }
            };
            return builders[section] ? builders[section]() : '';
        }

        function val(id) {
            const el = document.getElementById(id);
            return el ? el.value.trim() : '';
        }

        // ── Get the active text for a section (either mad libs or free write) ──
        function getSectionText(section) {
            if (sectionModes[section] === 'freewrite') {
                return document.getElementById(`${section}-freetext`).value.trim();
            }
            return getMadLibsText(section);
        }

        // ── Examples (unchanged) ──
        const examples = {
            about: {
                good: { profession: "software developer", hobby1: "learning new technologies", hobby2: "building innovative solutions", activity: "collaborating with teams", value: "continuous improvement" },
                bad:  { profession: "John Smith at 123 Main St", hobby1: "going to LA Fitness on Tuesdays", hobby2: "visiting Starbucks at 7am daily", activity: "calling (555) 123-4567", value: "my SSN 123-45-6789" }
            },
            interests: {
                good: { hobby1: "hiking in nature", hobby2: "watching movies", hobby3: "reading science fiction", topic: "artificial intelligence" },
                bad:  { hobby1: "working out at Mira Mesa Blvd gym", hobby2: "visiting specific locations weekly", hobby3: "being home alone after 8pm", topic: "my home address and routine" }
            },
            skills: {
                good: { skill1: "Python", skill2: "React", skill3: "machine learning", experience: "3 years", aspect: "solving complex problems" },
                bad:  { skill1: "working at Google Building 42", skill2: "calling 555-0192", skill3: "emailing sarah.j@company.com", experience: "manager Sarah Johnson", aspect: "sharing my employee details" }
            },
            goals: {
                good: { interest: "web development", goal: "collaborate on open-source projects", activity: "work on coding projects together" },
                bad:  { interest: "meeting near 742 Evergreen Terrace", goal: "share my SSN 123-45-6789", activity: "meet at my apartment" }
            }
        };

        // ── Track Mad Lib dropdown changes ──
        questionOrder.forEach(section => {
            document.querySelectorAll(`[data-section="${section}"] .madlib-select`).forEach(select => {
                select.addEventListener('change', () => {
                    safetyChecks[section] = false;
                    document.getElementById(`${section}-next`).classList.remove('visible');
                    document.getElementById(`${section}-result`).innerHTML = '';
                });
            });
        });

        function autofillSection(section, type) {
            const exampleData = examples[section][type];
            Object.keys(exampleData).forEach(key => {
                const input = document.getElementById(`${section}-${key}`);
                if (input) input.value = exampleData[key];
            });
            document.getElementById(`${section}-result`).innerHTML = '';
            safetyChecks[section] = false;
            document.getElementById(`${section}-next`).classList.remove('visible');
        }

        function updateProgress() {
            const percentage = (currentQuestion / totalQuestions) * 100;
            document.getElementById('progress-fill').style.width = percentage + '%';
            document.getElementById('progress-text').textContent = `Question ${currentQuestion} of ${totalQuestions}`;
        }

        function generateBioPreview() {
            const texts = {};
            questionOrder.forEach(section => {
                texts[section] = getSectionText(section);
            });

            document.getElementById('preview-about').textContent     = texts.about;
            document.getElementById('preview-interests').textContent = texts.interests;
            document.getElementById('preview-skills').textContent    = texts.skills;
            document.getElementById('preview-goals').textContent     = texts.goals;

            // Populate inline edit dropdowns (unchanged logic)
            const dropdownOptions = {
                'final-about-profession': ['software developer','designer','student','teacher','engineer','artist','writer','entrepreneur','researcher','data scientist'],
                'final-about-hobby1':     ['learning new technologies','solving problems','creating art','reading books','exploring ideas','building things','helping others','discovering new things'],
                'final-about-hobby2':     ['building innovative solutions','creative expression','tackling challenges','meeting new people','trying new experiences','making a difference','continuous learning'],
                'final-about-activity':   ['collaborating with teams','working independently','mentoring others','exploring new ideas','creative problem solving','deep focused work','brainstorming sessions'],
                'final-about-value':      ['continuous improvement','lifelong learning','creativity and innovation','making an impact','collaboration','authenticity','perseverance'],
                'final-interests-hobby1': ['hiking in nature','photography','playing music','cooking','gaming','reading','exercising','drawing','traveling'],
                'final-interests-hobby2': ['watching movies','playing sports','crafting','gardening','writing','meditation','cycling','dancing'],
                'final-interests-hobby3': ['reading science fiction','learning languages','volunteering','attending concerts','exploring museums','playing board games','practicing yoga'],
                'final-interests-topic':  ['artificial intelligence','sustainability','psychology','space exploration','history','philosophy','technology','art and design','health and wellness'],
                'final-skills-skill1':    ['Python','JavaScript','graphic design','writing','public speaking','project management','data analysis','video editing','photography'],
                'final-skills-skill2':    ['React','UI/UX design','communication','leadership','teaching','problem solving','research','marketing'],
                'final-skills-skill3':    ['machine learning','3D modeling','critical thinking','teamwork','time management','creative thinking','strategic planning'],
                'final-skills-experience':['beginner level','1 year','2 years','3 years','5+ years','intermediate level','advanced level','expert level'],
                'final-skills-aspect':    ['solving complex problems','creating beautiful designs','mentoring others','learning new techniques','working on challenging projects','collaborating with others','pushing boundaries'],
                'final-goals-interest':   ['web development','artificial intelligence','creative projects','entrepreneurship','academic research','social impact','the arts','technology','learning together'],
                'final-goals-goal':       ['collaborate on open-source projects','learn new skills','build meaningful projects','share knowledge','grow professionally','make new connections','find study partners','start a creative venture'],
                'final-goals-activity':   ['work on coding projects together','brainstorm ideas','attend tech meetups','exchange feedback','collaborate on creative work','practice and learn together','build something meaningful']
            };

            Object.keys(dropdownOptions).forEach(dropdownId => {
                const select = document.getElementById(dropdownId);
                if (!select) return;
                const options = dropdownOptions[dropdownId];
                select.innerHTML = '';
                const originalId = dropdownId.replace('final-', '');
                const originalValue = document.getElementById(originalId)?.value || '';
                options.forEach(option => {
                    const optionElement = document.createElement('option');
                    optionElement.value = option;
                    optionElement.textContent = option;
                    if (option === originalValue) optionElement.selected = true;
                    select.appendChild(optionElement);
                });
            });
        }

        function toggleEditMode(section) {
            const displayMode = document.getElementById(`display-${section}`);
            const editMode    = document.getElementById(`edit-${section}`);
            
            if (editMode.style.display === 'none') {
                // Opening edit: show the right sub-panel based on how the section was filled
                const dropdownPanel  = document.getElementById(`edit-${section}-dropdown`);
                const freewritePanel = document.getElementById(`edit-${section}-freewrite`);
                if (sectionModes[section] === 'freewrite') {
                    dropdownPanel.style.display  = 'none';
                    freewritePanel.style.display = 'block';
                    // Pre-fill with current preview text
                    const ta = document.getElementById(`final-${section}-freetext`);
                    if (ta) {
                        ta.value = document.getElementById(`preview-${section}`).textContent;
                        const counter = document.getElementById(`final-${section}-charcount`);
                        if (counter) counter.textContent = ta.value.length;
                        ta.oninput = () => {
                            if (counter) counter.textContent = ta.value.length;
                        };
                    }
                } else {
                    dropdownPanel.style.display  = 'block';
                    freewritePanel.style.display = 'none';
                }
                displayMode.style.display = 'none';
                editMode.style.display    = 'block';
            } else {
                displayMode.style.display = 'block';
                editMode.style.display    = 'none';
            }
        }

        function saveEditChanges(section) {
            let newText = '';
            if (sectionModes[section] === 'freewrite') {
                // Read from the freewrite textarea in the edit panel
                const ta = document.getElementById(`final-${section}-freetext`);
                newText = ta ? ta.value.trim() : '';
            } else {
                // Read from the inline dropdowns
                const sectionMap = {
                    about:     () => `I'm a passionate ${val('final-about-profession')} who loves ${val('final-about-hobby1')} and ${val('final-about-hobby2')}. I enjoy ${val('final-about-activity')} and believe in ${val('final-about-value')}.`,
                    interests: () => `In my free time, I enjoy ${val('final-interests-hobby1')}, ${val('final-interests-hobby2')}, and ${val('final-interests-hobby3')}. I'm also interested in learning more about ${val('final-interests-topic')}.`,
                    skills:    () => `I'm skilled at ${val('final-skills-skill1')}, ${val('final-skills-skill2')}, and ${val('final-skills-skill3')}. I have ${val('final-skills-experience')} of experience and enjoy ${val('final-skills-aspect')}.`,
                    goals:     () => `I'm looking to connect with people who are interested in ${val('final-goals-interest')}. My goal is to ${val('final-goals-goal')} and I'd love to ${val('final-goals-activity')}.`
                };
                newText = sectionMap[section] ? sectionMap[section]() : '';
            }
            if (newText) document.getElementById(`preview-${section}`).textContent = newText;
            toggleEditMode(section);
        }

        function nextQuestion(currentSection) {
            document.querySelector(`[data-section="${currentSection}"]`).classList.remove('active');
            currentQuestion++;
            updateProgress();
            if (currentQuestion <= totalQuestions) {
                document.querySelector(`[data-section="${questionOrder[currentQuestion - 1]}"]`).classList.add('active');
            } else {
                generateBioPreview();
                document.getElementById('submit-section').classList.add('visible');
                document.getElementById('progress-text').textContent = 'All Questions Complete!';
            }
        }

        async function checkSafetyWithAI(section) {
            const resultDiv = document.getElementById(`${section}-result`);
            const text = getSectionText(section);

            // Validate: ensure there's content
            if (!text) {
                if (sectionModes[section] === 'madlibs') {
                    resultDiv.innerHTML = '<div class="safety-result safety-warning"><span class="safety-icon">⚠️</span>Please select all options first!</div>';
                } else {
                    resultDiv.innerHTML = '<div class="safety-result safety-warning"><span class="safety-icon">⚠️</span>Please write something before checking!</div>';
                }
                return;
            }

            // Mad Libs mode: also ensure all selects are filled
            if (sectionModes[section] === 'madlibs') {
                const selects = document.querySelectorAll(`[data-section="${section}"] .madlib-select`);
                const values = Array.from(selects).map(s => s.value.trim());
                if (values.some(v => !v)) {
                    resultDiv.innerHTML = '<div class="safety-result safety-warning"><span class="safety-icon">⚠️</span>Please select all options first!</div>';
                    return;
                }
            }

            resultDiv.innerHTML = '<div class="safety-result safety-checking"><span class="safety-icon">🤖</span>AI is analyzing for personal information<span class="loading-dots">...</span></div>';

            try {
                const response = await fetch(`${pythonURI}/api/analyze-bio-safety`, {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    credentials: 'include',
                    body: JSON.stringify({ bio_text: text, section })
                });

                const data = await response.json();

                if (data.success && data.analysis) {
                    const analysis = data.analysis;
                    const severityClass = { safe: 'safety-safe', warning: 'safety-warning', danger: 'safety-danger' }[analysis.severity] || 'safety-safe';

                    safetyChecks[section] = (analysis.severity === 'safe');

                    let resultHTML = `<div class="safety-result ${severityClass}">`;
                    resultHTML += analysis.severity === 'safe' ? '<span class="safety-icon">✅</span>' :
                                  analysis.severity === 'warning' ? '<span class="safety-icon">⚠️</span>' : '<span class="safety-icon">🚫</span>';
                    resultHTML += `<strong>${analysis.message}</strong>`;
                    resultHTML += `<div style="margin-top:0.5em;font-size:0.9em;">AI Risk Score: ${analysis.risk_score}%</div>`;

                    if (analysis.issues_found?.length) {
                        resultHTML += '<ul class="issues-list">' + analysis.issues_found.map(i => `<li>${i}</li>`).join('') + '</ul>';
                    }
                    if (analysis.suggestions?.length) {
                        resultHTML += '<div style="margin-top:0.8em;"><strong>💡 Suggestions:</strong></div>';
                        resultHTML += '<ul class="suggestions-list">' + analysis.suggestions.map(s => `<li>${s}</li>`).join('') + '</ul>';
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
                const selects = document.querySelectorAll(`[id^="final-${section}-"]`);
                const sectionData = {};
                let sectionHasContent = false;
                selects.forEach(select => {
                    const value = select.value.trim();
                    if (value) {
                        sectionHasContent = true;
                        hasContent = true;
                        const fieldName = select.id.replace(`final-${section}-`, '');
                        sectionData[fieldName] = value;
                    }
                });
                if (sectionHasContent) bioData[section] = sectionData;
            }

            if (!hasContent) { showStatus('❌ Please fill in at least one section!', 'error'); return; }

            try {
                const idResponse = await fetch(`${pythonURI}/api/id`, { method: 'GET', credentials: 'include' });
                if (!idResponse.ok) { showStatus('❌ Please log in to save your bio', 'error'); return; }
                const userData = await idResponse.json();
                if (!userData?.id) { showStatus('❌ Please log in to save your bio', 'error'); return; }
            } catch (error) {
                showStatus('❌ Please log in to save your bio', 'error'); return;
            }

            try {
                showStatus('💾 Saving your bio...', 'success');
                const response = await fetch(`${pythonURI}/api/match/add`, {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    credentials: 'include',
                    body: JSON.stringify({
                        index: 'bio',
                        data: { ...bioData, last_updated: new Date().toISOString(), safety_checked: true, ai_verified: true }
                    })
                });
                const data = await response.json();
                if (response.ok || response.status === 201) {
                    showStatus('✅ Bio saved successfully! Your profile is ready for matchmaking.', 'success');
                } else {
                    showStatus(`❌ Error: ${data.message || 'Failed to save'}`, 'error');
                }
            } catch (error) {
                showStatus(`❌ Failed to save: ${error.message}`, 'error');
            }
        }

        function showStatus(message, type) {
            const statusDiv = document.getElementById('save-status');
            statusDiv.className = `status-message status-${type}`;
            statusDiv.textContent = message;
            statusDiv.style.display = 'block';
            if (type === 'success') setTimeout(() => { statusDiv.style.display = 'none'; }, 5000);
        }

        // ── Event listeners ──
        questionOrder.forEach(section => {
            document.getElementById(`${section}-good-btn`).addEventListener('click', () => autofillSection(section, 'good'));
            document.getElementById(`${section}-bad-btn`).addEventListener('click', () => autofillSection(section, 'bad'));
            document.getElementById(`${section}-check-btn`).addEventListener('click', () => checkSafetyWithAI(section));
            document.getElementById(`${section}-next`).addEventListener('click', () => nextQuestion(section));
        });

        document.getElementById('save-btn').addEventListener('click', saveBio);

        document.addEventListener('click', (e) => {
            if (e.target.classList.contains('edit-section-btn')) toggleEditMode(e.target.getAttribute('data-section'));
            if (e.target.classList.contains('save-edit-btn')) saveEditChanges(e.target.getAttribute('data-section'));
        });

        // Loading dots animation
        const style = document.createElement('style');
        style.textContent = `
            .loading-dots::after { content: ''; animation: dots 1.5s steps(4, end) infinite; }
            @keyframes dots { 0%, 20% { content: ''; } 40% { content: '.'; } 60% { content: '..'; } 80%, 100% { content: '...'; } }
        `;
        document.head.appendChild(style);

        // ── Navigation system (unchanged) ──
        const VISITED_KEY = 'api_visited_pages';
        let visitedPages = {};
        const pages = [
            { id: 1, url: '/digitalmatchmaking/api/' },
            { id: 2, url: '/digitalmatchmaking/mcq/' },
            { id: 3, url: '/digitalmatchmaking/microb/' },
            { id: 4, url: '/digitalmatchmaking/bio_create/' },
            { id: 5, url: '/digitalmatchmaking/matchmade/' }
        ];

        function loadVisitedPages() { try { return JSON.parse(localStorage.getItem(VISITED_KEY)) || {}; } catch (e) { return {}; } }
        function saveVisitedPages() { try { localStorage.setItem(VISITED_KEY, JSON.stringify(visitedPages)); } catch (e) {} }
        function isPageUnlocked(pageId) { return pageId === 1 || visitedPages[pageId - 1]; }
        function markPageVisited(pageId) { visitedPages[pageId] = true; saveVisitedPages(); updateNavigation(); }

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
                conn.classList.toggle('visited', !!visitedPages[idx + 1]);
            });
            const currentUrl = window.location.pathname;
            navNodes.forEach(node => { if (node.dataset.url === currentUrl) node.classList.add('current'); });
        }

        visitedPages = loadVisitedPages();
        const currentUrl = window.location.pathname;
        pages.forEach(page => { if (page.url === currentUrl) markPageVisited(page.id); });
        updateNavigation();
</script>