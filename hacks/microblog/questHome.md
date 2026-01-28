---
layout: page
description: Digital Matchmaking - go through the nodes to create your profile
permalink: /home/
breadcrumb: true
author: 
---

<!--Enhanced Network Style-->
<style type="text/css">
    * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
    }

    body {
        background: #0a0e27;
        color: #e0e0e0;
        font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }

    .mission-header {
        text-align: center;
        padding: 40px 20px;
        background: linear-gradient(135deg, #1a1f3a 0%, #0a0e27 100%);
        border-bottom: 2px solid #00d9ff;
        margin-bottom: 30px;
        position: relative;
        overflow: hidden;
    }

    .mission-header::before {
        content: '';
        position: absolute;
        top: 0;
        left: -100%;
        width: 100%;
        height: 100%;
        background: linear-gradient(90deg, transparent, rgba(0, 217, 255, 0.1), transparent);
        animation: scan 3s infinite;
    }

    @keyframes scan {
        0% { left: -100%; }
        100% { left: 100%; }
    }

    .glitch-text {
        font-size: 2.5em;
        font-weight: 700;
        color: #00d9ff;
        text-transform: uppercase;
        letter-spacing: 3px;
        text-shadow: 0 0 20px rgba(0, 217, 255, 0.5);
        margin-bottom: 20px;
        position: relative;
    }

    .mission-brief, .mission-objective {
        max-width: 800px;
        margin: 15px auto;
        line-height: 1.6;
        color: #b0b0b0;
        position: relative;
        z-index: 1;
    }

    .mission-objective {
        color: #00d9ff;
        font-weight: 500;
    }

    #comm_network {
        width: 100%;
        height: 700px;
        background: #0f1729;
        border: 2px solid #00d9ff;
        border-radius: 12px;
        position: relative;
        overflow: hidden;
        box-shadow: 0 10px 40px rgba(0, 217, 255, 0.3);
    }

    .warp-background {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        pointer-events: none;
        z-index: 1;
        overflow: hidden;
        perspective: 1200px;
        perspective-origin: center center;
    }

    .warp-grid {
        position: absolute;
        width: 200%;
        height: 200%;
        left: -50%;
        top: -50%;
        background-image: 
            repeating-linear-gradient(0deg, transparent, transparent 49px, rgba(0, 217, 255, 0.1) 49px, rgba(0, 217, 255, 0.1) 50px),
            repeating-linear-gradient(90deg, transparent, transparent 49px, rgba(0, 217, 255, 0.1) 49px, rgba(0, 217, 255, 0.1) 50px);
        background-size: 50px 50px;
        transform-style: preserve-3d;
        transition: transform 0.1s ease-out;
    }

    .scroll-wrapper {
        width: 100%;
        height: 100%;
        overflow-x: auto;
        overflow-y: hidden;
        cursor: default;
        scrollbar-width: none;
        -ms-overflow-style: none;
        position: relative;
        z-index: 2;
        perspective: 1200px;
        perspective-origin: center center;
    }

    .scroll-wrapper::-webkit-scrollbar {
        display: none;
    }

    .scroll-wrapper.grabbing {
        cursor: grabbing;
    }

    .network-container {
        position: relative;
        height: 100%;
        display: inline-block;
        min-width: 100%;
        transform-style: preserve-3d;
        pointer-events: none;
    }

    .network-canvas {
        height: 100%;
        position: relative;
        display: inline-block;
        transform-style: preserve-3d;
        transition: transform 0.1s ease-out;
        pointer-events: none;
    }

    .hints-panel {
        position: absolute;
        top: 20px;
        left: 20px;
        background: rgba(10, 14, 39, 0.95);
        border-radius: 8px;
        border: 1px solid #00d9ff;
        z-index: 10;
        backdrop-filter: blur(10px);
        max-width: 280px;
        box-shadow: 0 5px 20px rgba(0, 217, 255, 0.3);
    }

    .hints-toggle {
        padding: 12px 20px;
        cursor: pointer;
        user-select: none;
        display: flex;
        align-items: center;
        justify-content: space-between;
    }

    .hints-toggle:hover {
        background: rgba(0, 217, 255, 0.1);
    }

    .hints-title {
        color: #00d9ff;
        font-weight: 600;
        font-size: 0.95em;
        text-transform: uppercase;
        letter-spacing: 1px;
        display: flex;
        align-items: center;
        gap: 8px;
    }

    .hints-title::before {
        content: '❓';
        font-size: 1.2em;
    }

    .hints-arrow {
        color: #00d9ff;
        font-size: 0.8em;
        transition: transform 0.3s ease;
    }

    .hints-arrow.open {
        transform: rotate(180deg);
    }

    .hints-content {
        max-height: 0;
        overflow: hidden;
        transition: max-height 0.3s ease, padding 0.3s ease;
        padding: 0 20px;
    }

    .hints-content.open {
        max-height: 300px;
        padding: 0 20px 15px 20px;
    }

    .hint-item {
        color: #b0b0b0;
        font-size: 0.85em;
        line-height: 1.5;
        margin: 8px 0;
        padding-left: 15px;
        position: relative;
    }

    .hint-item::before {
        content: '→';
        position: absolute;
        left: 0;
        color: #00d9ff;
        font-weight: bold;
    }

    .network-legend {
        position: absolute;
        top: 150px;
        left: 20px;
        background: rgba(10, 14, 39, 0.9);
        padding: 15px 20px;
        border-radius: 8px;
        border: 1px solid #00d9ff;
        z-index: 10;
        backdrop-filter: blur(10px);
    }

    .legend-title {
        color: #00d9ff;
        font-weight: 600;
        margin-bottom: 10px;
        font-size: 0.9em;
        text-transform: uppercase;
        letter-spacing: 1px;
    }

    .legend-item {
        display: flex;
        align-items: center;
        margin: 8px 0;
        font-size: 0.85em;
        color: #b0b0b0;
    }

    .legend-dot {
        width: 12px;
        height: 12px;
        border-radius: 50%;
        margin-right: 10px;
        box-shadow: 0 0 10px currentColor;
    }

    .legend-dot.locked { background: #555; }
    .legend-dot.unlocked { background: #888; }
    .legend-dot.visited { background: #4caf50; }

    .node {
        position: absolute;
        width: 80px;
        height: 80px;
        border-radius: 50%;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        cursor: pointer;
        transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        z-index: 100;
        transform-origin: center;
        transform-style: preserve-3d;
        pointer-events: auto;
    }

    .node::before {
        content: '';
        position: absolute;
        width: 100%;
        height: 100%;
        border-radius: 50%;
        background: inherit;
        opacity: 0.3;
        animation: pulse 2s infinite;
    }

    @keyframes pulse {
        0%, 100% { transform: scale(1); opacity: 0.3; }
        50% { transform: scale(1.2); opacity: 0; }
    }

    .node.locked {
        background: linear-gradient(135deg, rgba(42, 42, 42, 0.4) 0%, rgba(26, 26, 26, 0.4) 100%);
        border: 2px solid rgba(68, 68, 68, 0.6);
        cursor: not-allowed;
        backdrop-filter: blur(5px);
    }

    .node.locked::before { animation: none; }

    .node.unlocked {
        background: linear-gradient(135deg, rgba(0, 217, 255, 0.15) 0%, rgba(0, 136, 255, 0.15) 100%);
        border: 2px solid rgba(0, 217, 255, 0.8);
        box-shadow: 0 0 20px rgba(0, 217, 255, 0.4);
        backdrop-filter: blur(5px);
    }

    .node.visited {
        background: linear-gradient(135deg, rgba(76, 175, 80, 0.2) 0%, rgba(56, 142, 60, 0.2) 100%);
        border: 2px solid rgba(102, 187, 106, 0.8);
        box-shadow: 0 0 20px rgba(76, 175, 80, 0.6);
        backdrop-filter: blur(5px);
    }

    .node:not(.locked):hover {
        transform: scale(1.15) translateY(-5px) translateZ(50px) !important;
        box-shadow: 0 10px 30px rgba(0, 217, 255, 0.6);
        z-index: 100;
    }

    .node.locked:hover {
        animation: shake 0.4s;
    }

    @keyframes shake {
        0%, 100% { transform: translateX(0); }
        25% { transform: translateX(-5px); }
        75% { transform: translateX(5px); }
    }

    .node-number {
        font-size: 1.5em;
        font-weight: 700;
        color: #fff;
        text-shadow: 0 2px 10px rgba(0, 0, 0, 0.5);
        margin-bottom: 5px;
    }

    .node-label {
        font-size: 0.7em;
        color: #e0e0e0;
        text-align: center;
        text-shadow: 0 1px 5px rgba(0, 0, 0, 0.7);
        font-weight: 500;
    }

    .connection-line {
        position: absolute;
        height: 3px;
        background: linear-gradient(90deg, #00d9ff 0%, #0088ff 100%);
        transform-origin: left center;
        z-index: 1;
        opacity: 0.6;
        box-shadow: 0 0 10px rgba(0, 217, 255, 0.5);
        pointer-events: none;
    }

    .connection-line.locked {
        background: linear-gradient(90deg, #444 0%, #333 100%);
        box-shadow: none;
        opacity: 0.3;
        pointer-events: none;
    }

    .node-card {
        position: absolute;
        pointer-events: none;
        display: none;
        min-width: 280px;
        max-width: 340px;
        background: linear-gradient(135deg, rgba(15, 23, 41, 0.98) 0%, rgba(26, 31, 58, 0.98) 100%);
        color: #fff;
        border-radius: 12px;
        border: 2px solid #00d9ff;
        box-shadow: 0 10px 40px rgba(0, 217, 255, 0.4);
        padding: 20px;
        z-index: 10000;
        font-family: 'Segoe UI', sans-serif;
        backdrop-filter: blur(10px);
        animation: slideIn 0.3s ease-out;
    }

    @keyframes slideIn {
        from {
            opacity: 0;
            transform: translateY(-10px);
        }
        to {
            opacity: 1;
            transform: translateY(0);
        }
    }

    .node-card .card-title {
        font-size: 1.3em;
        font-weight: 600;
        color: #00d9ff;
        margin-bottom: 12px;
        text-shadow: 0 0 10px rgba(0, 217, 255, 0.5);
    }

    .node-card .card-description {
        line-height: 1.5;
        color: #b0b0b0;
        margin-bottom: 15px;
        font-size: 0.95em;
    }

    .node-card .tags {
        display: flex;
        flex-wrap: wrap;
        gap: 8px;
    }

    .node-card .tag {
        background: rgba(0, 217, 255, 0.15);
        border: 1px solid rgba(0, 217, 255, 0.3);
        padding: 5px 12px;
        border-radius: 15px;
        font-size: 0.8em;
        color: #00d9ff;
        font-weight: 500;
    }

    .progress-bar {
        display: none;
    }

    .progress-label {
        display: none;
    }

    .progress-track {
        display: none;
    }

    .progress-fill {
        display: none;
    }

    .progress-text {
        display: none;
    }

    @media (max-width: 768px) {
        .glitch-text { font-size: 1.8em; }
        #comm_network { height: 500px; }
        .node { width: 60px; height: 60px; }
        .node-number { font-size: 1.2em; }
        .node-label { font-size: 0.6em; }
        .hints-panel { font-size: 0.8em; max-width: 200px; }
        .network-legend { font-size: 0.8em; }
        .progress-bar { width: 80%; }
    }
</style>

<!--Network Container-->
<div id="comm_network">
    <div class="warp-background">
        <div class="warp-grid" id="warpGrid"></div>
    </div>
    
    <div class="hints-panel">
        <div class="hints-toggle" id="hintsToggle">
            <div class="hints-title">Help</div>
            <div class="hints-arrow" id="hintsArrow">▼</div>
        </div>
        <div class="hints-content" id="hintsContent">
            <div class="hint-item">Complete nodes in sequential order</div>
            <div class="hint-item">Scroll horizontally to view all nodes</div>
            <div class="hint-item">Hover over nodes for details</div>
            <div class="hint-item">Previous node must be completed to unlock next</div>
        </div>
    </div>

    <div class="network-legend">
        <div class="legend-title">Network Status</div>
        <div class="legend-item">
            <div class="legend-dot locked"></div>
            <span>Locked</span>
        </div>
        <div class="legend-item">
            <div class="legend-dot unlocked"></div>
            <span>Available</span>
        </div>
        <div class="legend-item">
            <div class="legend-dot visited"></div>
            <span>Completed</span>
        </div>
    </div>
    
    <div class="scroll-wrapper" id="scrollWrapper">
        <div class="network-container" id="networkContainer">
            <div class="network-canvas" id="networkCanvas"></div>
        </div>
    </div>
    
    <div class="node-card" id="nodeCard"></div>
</div>

<!--Network Script-->
<script>
(function() {
    const nodes = [
        {
            id: 1, 
            label: 'API Blog', 
            url: '/digitalmatchmaking/api/',
            longTitle: 'Comm Relay Alpha',
            description: 'Primary uplink relay. Repairs required to restore long-range communications.',
            tags: ['relay', 'priority-high', 'uplink']
        },

        {
            id: 2, 
            label: 'PII Quiz', 
            url: '/digitalmatchmaking/mcq/',
            longTitle: 'Tactical Beacon Beta',
            description: 'Short-range beacon used for local operative coordination and security verification.',
            tags: ['beacon', 'local', 'security']
        },
        {
            id: 3, 
            label: 'Microblog', 
            url: '/digitalmatchmaking/microb/',
            longTitle: 'Orbital Hub Gamma',
            description: 'Orbital hub with degraded power systems. Critical for network synchronization.',
            tags: ['orbital', 'maintenance', 'power-sys']
        },
        {
            id: 4, 
            label: 'Bio Creation', 
            url: '/digitalmatchmaking//bio_create/',
            longTitle: 'Backup Array Epsilon',
            description: 'Cold backup array. Bring spare modules to reactivate routing protocols.',
            tags: ['backup', 'spare-parts', 'routing']
        },
        {
            id: 5, 
            label: 'Matchmade', 
            url: '/digitalmatchmaking/matchmade/',
            longTitle: 'Integration Module Zeta',
            description: 'Final integration module. Complete sequence to restore full network functionality.',
            tags: ['integration', 'final-stage', 'critical']
        }
    ];

    const VISITED_KEY = 'microblog_visited_nodes';
    let visitedMap = {};

    // Load visited state
    function loadVisited() {
        try {
            return JSON.parse(localStorage.getItem(VISITED_KEY)) || {};
        } catch (e) {
            return {};
        }
    }

    function saveVisited() {
        try {
            localStorage.setItem(VISITED_KEY, JSON.stringify(visitedMap));
        } catch (e) {}
    }

    function isUnlocked(nodeId) {
        if (nodeId === 1) return true;
        return visitedMap[nodeId - 1];
    }

    function markVisited(nodeId) {
        visitedMap[nodeId] = true;
        saveVisited();
        updateNodeStates();
        updateProgress();
    }

    function updateProgress() {
        // Progress bar removed - function kept for compatibility
    }

    function updateNodeStates() {
        nodes.forEach(node => {
            const el = document.getElementById('node-' + node.id);
            if (!el) return;
            
            el.className = 'node';
            if (visitedMap[node.id]) {
                el.classList.add('visited');
            } else if (isUnlocked(node.id)) {
                el.classList.add('unlocked');
            } else {
                el.classList.add('locked');
            }
        });

        for (let i = 0; i < nodes.length - 1; i++) {
            const line = document.getElementById('line-' + i);
            if (line) {
                if (visitedMap[nodes[i].id]) {
                    line.classList.remove('locked');
                } else {
                    line.classList.add('locked');
                }
            }
        }
    }

    function createNetwork() {
        console.log('Creating network...');
        const canvas = document.getElementById('networkCanvas');
        const card = document.getElementById('nodeCard');
        const container = document.getElementById('comm_network');
        const scrollWrapper = document.getElementById('scrollWrapper');
        const networkContainer = document.getElementById('networkContainer');
        
        console.log('Elements found:', {canvas, card, container, scrollWrapper, networkContainer});
        
        // Create nodes in linear arrangement - centered vertically
        const startX = 150;
        const spacing = 200;
        const yBase = 350; // Keep centered
        const yVariation = 0; // Remove vertical variation to center nodes

        // Get viewport width
        const viewportWidth = scrollWrapper.clientWidth;
        
        // Calculate positions
        const lastNodeX = startX + (nodes.length - 1) * spacing;
        const nodeWidth = 80;
        
        // Canvas width: just enough to fit last node with padding, but not excessive
        const canvasWidth = lastNodeX + nodeWidth + 150;
        
        // Container width: viewport + distance to last node
        const containerWidth = Math.max(viewportWidth, canvasWidth);
        
        canvas.style.width = canvasWidth + 'px';
        networkContainer.style.width = containerWidth + 'px';

        console.log('Canvas dimensions:', {canvasWidth, containerWidth, viewportWidth});

        // Create connection lines
        for (let i = 0; i < nodes.length - 1; i++) {
            const node1 = nodes[i];
            const node2 = nodes[i + 1];
            
            const x1 = startX + (i * spacing);
            const x2 = startX + ((i + 1) * spacing);
            const y1 = yBase + (i % 2 === 0 ? yVariation : -yVariation);
            const y2 = yBase + ((i + 1) % 2 === 0 ? yVariation : -yVariation);
            
            const line = document.createElement('div');
            line.id = 'line-' + i;
            line.className = 'connection-line';
            
            const length = Math.sqrt(Math.pow(x2 - x1, 2) + Math.pow(y2 - y1, 2));
            const angle = Math.atan2(y2 - y1, x2 - x1) * (180 / Math.PI);
            
            line.style.width = length + 'px';
            line.style.left = x1 + 40 + 'px';
            line.style.top = y1 + 40 + 'px';
            line.style.transform = `rotate(${angle}deg) translateZ(-50px)`; // Push lines behind nodes
            line.style.transformStyle = 'preserve-3d';
            
            canvas.appendChild(line);
        }

        // Create nodes
        nodes.forEach((node, index) => {
            console.log('Creating node:', node.id, node.label);
            const nodeEl = document.createElement('div');
            nodeEl.id = 'node-' + node.id;
            nodeEl.className = 'node';
            
            const x = startX + (index * spacing);
            const y = yBase + (index % 2 === 0 ? yVariation : -yVariation);
            
            nodeEl.style.left = x + 'px';
            nodeEl.style.top = y + 'px';
            
            console.log('Node position:', {id: node.id, x, y});
            
            nodeEl.innerHTML = `
                <div class="node-number">${node.id}</div>
                <div class="node-label">${node.label}</div>
            `;

            nodeEl.addEventListener('mouseenter', (e) => {
                console.log('Mouse entered node:', node.id);
                const rect = container.getBoundingClientRect();
                const nodeRect = nodeEl.getBoundingClientRect();
                const x = nodeRect.left - rect.left + 40; // Center of node
                const y = nodeRect.top - rect.top + 40;
                
                console.log('Card position:', {x, y, rectWidth: rect.width, rectHeight: rect.height});
                
                card.innerHTML = `
                    <div class="card-title">${node.longTitle}</div>
                    <div class="card-description">${node.description}</div>
                    <div class="tags">
                        ${node.tags.map(tag => `<span class="tag">${tag}</span>`).join('')}
                    </div>
                `;
                
                card.style.left = Math.min(rect.width - 360, x + 20) + 'px';
                card.style.top = Math.min(rect.height - 200, y + 20) + 'px';
                card.style.display = 'block';
                card.style.pointerEvents = 'none';
                console.log('Card display set to block, styles:', card.style.left, card.style.top);
            });

            nodeEl.addEventListener('mouseleave', () => {
                console.log('Mouse left node:', node.id);
                card.style.display = 'none';
            });

            nodeEl.addEventListener('click', () => {
                console.log('Node clicked:', node.id, 'Unlocked:', isUnlocked(node.id));
                if (isUnlocked(node.id)) {
                    console.log('Navigating to:', node.url);
                    markVisited(node.id);
                    window.location.href = node.url;
                } else {
                    console.log('Node is locked');
                }
            });

            canvas.appendChild(nodeEl);
        });

        // Enforce scroll limit
        const maxScrollLeft = canvasWidth - viewportWidth;
        
        scrollWrapper.addEventListener('scroll', function(e) {
            if (this.scrollLeft > maxScrollLeft) {
                this.scrollLeft = maxScrollLeft;
            }
            if (this.scrollLeft < 0) {
                this.scrollLeft = 0;
            }
        });

        updateNodeStates();
        updateProgress();
    }

    // Initialize
    visitedMap = loadVisited();
    createNetwork();

    // Handle drag scrolling manually
    const scrollWrapper = document.getElementById('scrollWrapper');
    let isDragging = false;
    let startX;
    let scrollLeft;
    let hasMoved = false;

    scrollWrapper.addEventListener('mousedown', (e) => {
        console.log('Mousedown on scrollWrapper, target:', e.target);
        // Don't start drag if clicking on a node
        if (e.target.closest('.node')) {
            console.log('Clicked on node, not starting drag');
            return;
        }
        isDragging = true;
        hasMoved = false;
        scrollWrapper.classList.add('grabbing');
        scrollWrapper.style.cursor = 'grabbing';
        startX = e.pageX - scrollWrapper.offsetLeft;
        scrollLeft = scrollWrapper.scrollLeft;
        console.log('Started dragging');
    });

    scrollWrapper.addEventListener('mouseleave', () => {
        console.log('Mouse left scrollWrapper');
        isDragging = false;
        scrollWrapper.classList.remove('grabbing');
        scrollWrapper.style.cursor = 'default';
    });

    scrollWrapper.addEventListener('mouseup', (e) => {
        console.log('Mouseup, isDragging:', isDragging, 'hasMoved:', hasMoved);
        isDragging = false;
        scrollWrapper.classList.remove('grabbing');
        scrollWrapper.style.cursor = 'default';
    });

    scrollWrapper.addEventListener('mousemove', (e) => {
        if (!isDragging) return;
        e.preventDefault();
        hasMoved = true;
        const x = e.pageX - scrollWrapper.offsetLeft;
        const walk = (x - startX) * 2;
        scrollWrapper.scrollLeft = scrollLeft - walk;
    });

    // Dropdown toggle for hints
    const hintsToggle = document.getElementById('hintsToggle');
    const hintsContent = document.getElementById('hintsContent');
    const hintsArrow = document.getElementById('hintsArrow');
    
    hintsToggle.addEventListener('click', () => {
        hintsContent.classList.toggle('open');
        hintsArrow.classList.toggle('open');
    });

    // Warp background effect
    const container = document.getElementById('comm_network');
    const warpGrid = document.getElementById('warpGrid');
    let mouseX = 0, mouseY = 0;
    let currentX = 0, currentY = 0;

    container.addEventListener('mousemove', (e) => {
        const rect = container.getBoundingClientRect();
        mouseX = (e.clientX - rect.left) / rect.width;
        mouseY = (e.clientY - rect.top) / rect.height;
    });

    function animateWarp() {
        // Faster interpolation to reduce lag
        currentX += (mouseX - 0.5 - currentX) * 0.15;
        currentY += (mouseY - 0.5 - currentY) * 0.15;

        // Very subtle angles with minimal up/down tilt
        const rotateX = -8 + (currentY * 3); // Minimal tilt: -9.5 to -6.5 degrees
        const rotateY = currentX * 15; // Moderate side-to-side rotation
        const rotateZ = 0; // No roll

        // Apply to background grid - push it back further
        warpGrid.style.transform = `
            rotateX(${rotateX}deg)
            rotateY(${rotateY}deg)
            rotateZ(${rotateZ}deg)
            translateZ(-200px)
        `;

        // Apply same transform to canvas and nodes - keep them closer to camera
        const canvas = document.getElementById('networkCanvas');
        canvas.style.transform = `
            rotateX(${rotateX}deg)
            rotateY(${rotateY}deg)
            rotateZ(${rotateZ}deg)
            translateZ(-180px)
        `;

        // Give nodes individual depth based on their Y position
        nodes.forEach((node, index) => {
            const nodeEl = document.getElementById('node-' + node.id);
            if (!nodeEl) return;
            
            // Smaller depth variation for subtle effect
            const baseDepth = (index % 2 === 0 ? 15 : -15);
            
            // Reset any hover transforms and apply only depth
            if (!nodeEl.matches(':hover')) {
                nodeEl.style.transform = `translateZ(${baseDepth}px)`;
            }
        });

        requestAnimationFrame(animateWarp);
    }

    animateWarp();

    // Reset warp on mouse leave
    container.addEventListener('mouseleave', () => {
        mouseX = 0.5;
        mouseY = 0.5;
    });
})();
</script>