<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Zab AI - Complete Safety Hub</title>
    <style>
        * { box-sizing: border-box; margin: 0; padding: 0; font-family: 'Segoe UI', system-ui, sans-serif; }
        body { background-color: #121212; display: flex; flex-direction: column; align-items: center; justify-content: center; min-height: 100vh; padding: 10px; color: #fff; }
        
        /* App Branding Header */
        .brand-header { text-align: center; margin-bottom: 15px; width: 100%; max-width: 360px; }
        .logo-box { width: 110px; height: 110px; background-color: #121212; margin: 0 auto 10px; border-radius: 22px; border: 3px solid #333; display: flex; align-items: center; justify-content: center; position: relative; box-shadow: 0 4px 15px rgba(0,0,0,0.6); overflow: hidden; }
        
        /* Custom Neon Glass Shield Design Vector Definition */
        .logo-svg { width: 90px; height: 90px; filter: drop-shadow(0px 0px 8px #FF007F); }
        .brand-title { font-size: 26px; font-weight: bold; letter-spacing: 1px; background: linear-gradient(45deg, #FF007F, #93C572, #AEC6CF); -webkit-background-clip: text; -webkit-text-fill-color: transparent; }
        
        /* Smartphone Device Frame Container */
        .phone-shell { width: 100%; max-width: 360px; height: 600px; background-color: #1a1a1a; border: 4px solid #333; border-radius: 28px; display: flex; flex-direction: column; overflow: hidden; position: relative; box-shadow: 0 15px 35px rgba(0,0,0,0.6); }
        .system-status { background-color: #121212; padding: 6px 16px; display: flex; justify-content: space-between; align-items: center; font-size: 11px; font-weight: bold; color: #AEC6CF; }
        .app-bar { background-color: #222; padding: 12px 16px; display: flex; justify-content: space-between; align-items: center; border-bottom: 1px solid #333; }
        .app-bar h1 { font-size: 16px; font-weight: bold; color: #AEC6CF; }
        .tier-select { background: #333; color: #93C572; border: 1px solid #444; padding: 4px 6px; font-weight: bold; border-radius: 4px; font-size: 11px; cursor: pointer; }
        
        /* Main Workspace Container */
        .app-body { flex: 1; padding: 20px; display: flex; flex-direction: column; background-color: #151515; overflow-y: auto; }
        .pane { display: none; height: 100%; width: 100%; flex-direction: column; align-items: center; justify-content: center; }
        .pane.active { display: flex; }
        
        /* Variant 1: SOS Button Core */
        .sos-core { width: 140px; height: 140px; background: radial-gradient(circle, #ff1744, #d50000); border-radius: 50%; display: flex; align-items: center; justify-content: center; color: white; font-size: 32px; font-weight: bold; cursor: pointer; box-shadow: 0 0 20px rgba(213,0,0,0.5); border: 4px solid #FF007F; user-select: none; }
        .sos-subtext { margin-top: 20px; color: #aaa; font-size: 12px; text-align: center; line-height: 1.4; }
        
        /* Variant 2: Guard Grid Matrices */
        .matrix-title { font-size: 16px; font-weight: bold; color: #93C572; align-self: flex-start; margin-bottom: 12px; }
        .matrix-card { background: #222; width: 100%; padding: 12px; border-radius: 8px; margin-bottom: 8px; display: flex; align-items: center; border-left: 4px solid #93C572; font-size: 13px; color: #ddd; }
        
        /* Variant 3: Gemini Vision Core */
        .token-hud { font-size: 14px; font-weight: bold; color: #AEC6CF; margin-bottom: 12px; }
        .camera-radar { width: 100%; height: 130px; background-color: #121212; border-radius: 12px; position: relative; overflow: hidden; display: flex; align-items: center; justify-content: center; color: #666; font-size: 12px; border: 2px dashed #333; margin-bottom: 15px; }
        .laser-beam { width: 100%; height: 3px; background-color: #93C572; position: absolute; top: 0; left: 0; box-shadow: 0 0 8px #93C572; animation: scanning 2s infinite ease-in-out; display: none; }
        @keyframes scanning { 0% { top: 0%; } 50% { top: 100%; } 100% { top: 0%; } }
        .action-btn { background: linear-gradient(45deg, #37474F, #222); color: white; border: 1px solid #444; padding: 12px; font-weight: bold; border-radius: 8px; width: 100%; cursor: pointer; }
        
        /* Bottom Navigation Bar Layout */
        .bottom-nav { height: 56px; background-color: #222; border-top: 1px solid #333; display: flex; }
        .nav-node { flex: 1; display: flex; flex-direction: column; align-items: center; justify-content: center; color: #888; font-size: 11px; font-weight: bold; cursor: pointer; }
        .nav-node.active { color: #FF007F; }
        .icon-slot { font-size: 18px; margin-bottom: 2px; }
        
        /* Legal Shield Disclaimer Window Pop-up */
        .shield-modal { position: absolute; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.9); display: flex; align-items: center; justify-content: center; padding: 20px; z-index: 100; }
        .box-disclaimer { background: #222; border-radius: 16px; padding: 20px; border-top: 6px solid #FF007F; text-align: center; }
        .box-disclaimer h2 { font-size: 15px; color: #FF007F; margin-bottom: 10px; }
        .box-disclaimer p { font-size: 11px; color: #bbb; line-height: 1.5; margin-bottom: 15px; }
        .btn-confirm { background-color: #FF007F; color: white; border: none; padding: 10px; border-radius: 6px; font-weight: bold; width: 100%; cursor: pointer; }
        .toast-popup { background: #FF007F; color: white; padding: 10px; border-radius: 4px; font-size: 12px; position: absolute; bottom: 70px; left: 16px; right: 16px; display: none; z-index: 90; text-align: center; }
    </style>
</head>
<body>

    <!-- Upper Brand Shell -->
    <div class="brand-header">
        <div class="logo-box">
            <!-- Vector Matrix of your exact custom Cyber-Shield Logo -->
            <svg class="logo-svg" viewBox="0 0 100 100" xmlns="http://w3.org">
                <!-- Layer 4: Matte Black Subtle Outer Base Shield Chassis -->
                <path d="M50,10 C70,18 85,15 85,45 C85,70 65,85 50,90 C35,85 15,70 15,45 C15,15 30,18 50,10 Z" fill="#151515" stroke="#333" stroke-width="2"/>
                <!-- Layer 3: Pastel Blue Structural Framing Shield Curve -->
                <path d="M50,15 C66,22 78,20 78,45 C78,66 62,79 50,84 C38,79 22,66 22,45 C22,20 34,22 50,15 Z" fill="none" stroke="#AEC6CF" stroke-width="3" opacity="0.8"/>
                <!-- Layer 2: Pista Green Neon Circuit Glow Inner Frame -->
                <path d="M50,22 C62,28 72,26 72,45 C72,62 59,73 50,77 C41,73 28,62 28,45 C28,26 38,28 50,22 Z" fill="none" stroke="#93C572" stroke-width="2" stroke-dasharray="4,2"/>
                <!-- Layer 1: Bright Neon Pink Monogram Tugh Core (Fusing Z, A, B lines) -->
                <path d="M40,32 L60,32 L40,55 L60,55 M40,55 L50,32 L60,55 M42,48 L58,48 M45,35 C42,42 42,50 45,55" fill="none" stroke="#FF007F" stroke-width="4" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
        </div>
        <div class="brand-title">ZAB AI</div>
    </div>

    <!-- Smartphone UI Emulation Node -->
    <div class="phone-shell">
        
        <!-- Legal Notice Screen Shield Overlay -->
        <div class="shield-modal" id="disclaimerModal">
            <div class="box-disclaimer">
                <h2>⚖️ Legal Notice Notice (Zab AI Shield)</h2>
                <p>This tracking application is fully compliant with the Indian DPDP Act, 2023. It does NOT offer formal medical advice. Always cross-verify scanner readouts with certified human adults.</p>
                <button class="btn-confirm" onclick="clearModal()">I AGREE & CONFIRM</button>
            </div>
        </div>

        <div class="system-status">
            <span>🔴 AIRTEL TRANSITION GATEWAY ACTIVE</span>
            <span>21:30</span>
        </div>

        <div class="app-bar">
            <h1 id="headerTitle">AI Alpha Hub</h1>
            <select class="tier-select" onchange="toggleAppTier(this.value)">
                <option value="AI Z">AI Z (₹49/mo)</option>
                <option value="AI Alpha" selected>AI Alpha (₹79/mo)</option>
                <option value="AI Beta">AI Beta (₹119/mo)</option>
            </select>
        </div>

        <div class="app-body">
            <!-- VARIETY 1 PAGE: SOS DASHBOARD -->
            <div class="pane active" id="pane-sos">
                <div class="sos-core" onclick="runSOS()">SOS</div>
                <p class="sos-subtext">One-tap coordinate synchronization platform. Broadcasting live tracking data strings directly to separate guardian accounts.</p>
            </div>

            <!-- VARIETY 2 PAGE: GUARD NET MATRIX -->
            <div class="pane" id="pane-guard">
                <p class="matrix-title" id="matrixLabel">AI Alpha Guard Log</p>
                <div id="matrixBox" style="width: 100%;"></div>
            </div>

            <!-- VARIETY 3 PAGE: AI SCANNERS PANEL -->
            <div class="pane" id="pane-scan">
                <p class="token-hud" id="tokenLabel">Tokens Remaining: 15 / 15</p>
                <div class="camera-radar" id="radar">
                    <div class="laser-beam" id="laserBeam"></div>
                    <span id="radarText">[👁️ GEMINI CAMERA RADAR IDLE]</span>
                </div>
                <button class="action-btn" onclick="runCameraScan()">Execute Bottle Scan</button>
            </div>
        </div>

        <div class="toast-popup" id="toast">Transition logged.</div>

        <!-- Lower Navigation Bar Layout -->
        <div class="bottom-nav">
            <div class="nav-node active" id="btn-sos" onclick="navigateTab(0)">
                <div class="icon-slot">⚠️</div>
                <span>SOS Trigger</span>
            </div>
            <div class="nav-node" id="btn-guard" onclick="navigateTab(1)">
# ZAB-AI-
this app use to safeguard your self 
