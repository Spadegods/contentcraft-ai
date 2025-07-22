<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ContentCraft AI</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            background: #1a1a1a;
            color: white;
            min-height: 100vh;
            overflow-x: hidden;
        }

        .container {
            max-width: 400px;
            margin: 0 auto;
            padding: 20px;
            min-height: 100vh;
        }

        .header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }

        .back-btn {
            background: none;
            border: none;
            color: white;
            font-size: 18px;
            cursor: pointer;
            padding: 8px;
        }

        .customize-btn {
            background: white;
            color: #1a1a1a;
            border: none;
            padding: 8px 16px;
            border-radius: 20px;
            font-weight: 500;
            cursor: pointer;
        }

        .app-header {
            background: linear-gradient(135deg, #8B5CF6 0%, #3B82F6 100%);
            padding: 20px;
            border-radius: 15px;
            margin-bottom: 20px;
            position: relative;
            overflow: hidden;
        }

        .app-header::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: linear-gradient(45deg, rgba(255,255,255,0.1) 0%, rgba(255,255,255,0) 100%);
            pointer-events: none;
        }

        .app-info {
            display: flex;
            align-items: center;
            gap: 15px;
            margin-bottom: 15px;
        }

        .app-icon {
            width: 50px;
            height: 50px;
            background: rgba(255,255,255,0.2);
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 24px;
        }

        .app-details h1 {
            font-size: 24px;
            font-weight: 700;
            margin-bottom: 4px;
        }

        .app-details p {
            opacity: 0.9;
            font-size: 14px;
        }

        .plan-info {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .plan-text {
            font-size: 14px;
            opacity: 0.9;
        }

        .upgrade-btn {
            background: linear-gradient(135deg, #EC4899 0%, #8B5CF6 100%);
            color: white;
            border: none;
            padding: 8px 16px;
            border-radius: 20px;
            font-weight: 600;
            cursor: pointer;
            transition: transform 0.2s;
        }

        .upgrade-btn:hover {
            transform: scale(1.05);
        }

        .main-content {
            background: linear-gradient(135deg, #8B5CF6 0%, #3B82F6 100%);
            padding: 25px;
            border-radius: 15px;
            margin-bottom: 20px;
        }

        .section-title {
            font-size: 20px;
            font-weight: 700;
            margin-bottom: 20px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .input-group {
            margin-bottom: 20px;
        }

        .input-label {
            display: block;
            margin-bottom: 8px;
            font-weight: 500;
        }

        .topic-input {
            width: 100%;
            padding: 12px;
            border: none;
            border-radius: 8px;
            background: rgba(255,255,255,0.1);
            color: white;
            font-size: 16px;
            backdrop-filter: blur(10px);
        }

        .topic-input::placeholder {
            color: rgba(255,255,255,0.6);
        }

        .topic-input:focus {
            outline: none;
            background: rgba(255,255,255,0.2);
        }

        .options-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 10px;
            margin-bottom: 20px;
        }

        .option-btn {
            background: rgba(255,255,255,0.1);
            border: 2px solid transparent;
            color: white;
            padding: 12px 8px;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.2s;
            display: flex;
            align-items: center;
            gap: 8px;
            font-size: 14px;
            font-weight: 500;
        }

        .option-btn:hover {
            background: rgba(255,255,255,0.2);
        }

        .option-btn.selected {
            background: rgba(255,255,255,0.2);
            border-color: rgba(255,255,255,0.5);
        }

        .tiktok-btn {
            grid-column: 1 / 2;
        }

        .tone-grid {
            display: grid;
            grid-template-columns: 1fr 1fr 1fr;
            gap: 8px;
            margin-bottom: 20px;
        }

        .tone-btn {
            background: rgba(255,255,255,0.1);
            border: 2px solid transparent;
            color: white;
            padding: 10px 8px;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.2s;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 4px;
            font-size: 12px;
            font-weight: 500;
        }

        .tone-btn:hover {
            background: rgba(255,255,255,0.2);
        }

        .tone-btn.selected {
            background: rgba(255,255,255,0.2);
            border-color: rgba(255,255,255,0.5);
        }

        .generate-btn {
            width: 100%;
            background: linear-gradient(135deg, #EC4899 0%, #8B5CF6 100%);
            color: white;
            border: none;
            padding: 15px;
            border-radius: 12px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            transition: transform 0.2s;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
        }

        .generate-btn:hover {
            transform: scale(1.02);
        }

        .generate-btn:disabled {
            opacity: 0.6;
            cursor: not-allowed;
            transform: none;
        }

        .loading {
            display: none;
            width: 20px;
            height: 20px;
            border: 2px solid rgba(255,255,255,0.3);
            border-top: 2px solid white;
            border-radius: 50%;
            animation: spin 1s linear infinite;
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        .content-display {
            background: linear-gradient(135deg, #8B5CF6 0%, #3B82F6 100%);
            padding: 25px;
            border-radius: 15px;
            margin-bottom: 20px;
            min-height: 200px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
        }

        .content-display.has-content {
            justify-content: flex-start;
            align-items: stretch;
        }

        .placeholder {
            text-align: center;
            opacity: 0.7;
        }

        .target-icon {
            width: 60px;
            height: 60px;
            background: linear-gradient(135deg, #EF4444 0%, #DC2626 100%);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 15px;
            position: relative;
        }

        .target-icon::before {
            content: '';
            position: absolute;
            width: 40px;
            height: 40px;
            border: 3px solid white;
            border-radius: 50%;
        }

        .target-icon::after {
            content: '';
            position: absolute;
            width: 20px;
            height: 20px;
            background: white;
            border-radius: 50%;
        }

        .arrow {
            position: absolute;
            top: 5px;
            right: 8px;
            width: 0;
            height: 0;
            border-left: 8px solid #60A5FA;
            border-top: 4px solid transparent;
            border-bottom: 4px solid transparent;
        }

        .generated-content {
            background: rgba(255,255,255,0.1);
            padding: 20px;
            border-radius: 12px;
            margin-bottom: 15px;
            line-height: 1.6;
            word-wrap: break-word;
            white-space: pre-wrap; /* Ensures newlines from '\n' are respected */
        }

        .content-actions {
            display: flex;
            gap: 10px;
            margin-top: 15px;
        }

        .action-btn {
            flex: 1;
            background: rgba(255,255,255,0.1);
            border: 1px solid rgba(255,255,255,0.3);
            color: white;
            padding: 10px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 14px;
            transition: all 0.2s;
        }

        .action-btn:hover {
            background: rgba(255,255,255,0.2);
        }

        .features-section {
            background: linear-gradient(135deg, #8B5CF6 0%, #3B82F6 100%);
            padding: 25px;
            border-radius: 15px;
        }

        .features-title {
            font-size: 20px;
            font-weight: 700;
            margin-bottom: 20px;
            text-align: center;
        }

        .feature-card {
            background: rgba(255,255,255,0.1);
            padding: 20px;
            border-radius: 12px;
            margin-bottom: 15px;
            text-align: center;
        }

        .feature-icon {
            font-size: 24px;
            margin-bottom: 10px;
        }

        .feature-title {
            font-size: 16px;
            font-weight: 600;
            margin-bottom: 8px;
        }

        .feature-description {
            font-size: 14px;
            opacity: 0.9;
            line-height: 1.4;
        }

        .usage-counter {
            background: rgba(255,255,255,0.1);
            padding: 10px 15px;
            border-radius: 8px;
            font-size: 14px;
            margin-bottom: 15px;
            text-align: center;
        }

        .hidden {
            display: none;
        }

        .page {
            display: none;
        }

        .page.active {
            display: block;
        }

        .content-type-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 10px;
            margin-bottom: 20px;
        }

        .content-type-btn {
            background: rgba(255,255,255,0.1);
            border: 2px solid transparent;
            color: white;
            padding: 15px 10px;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.2s;
            display: flex;
            align-items: center;
            gap: 8px;
            font-size: 14px;
            font-weight: 500;
        }

        .content-type-btn:hover {
            background: rgba(255,255,255,0.2);
        }

        .content-type-btn.selected {
            background: rgba(255,255,255,0.2);
            border-color: rgba(255,255,255,0.5);
        }

        .hashtags-only {
            grid-column: 1 / 2;
        }

        .toast {
            position: fixed;
            top: 20px;
            right: 20px;
            background: #10B981;
            color: white;
            padding: 12px 20px;
            border-radius: 8px;
            transform: translateX(100%);
            transition: transform 0.3s ease;
            z-index: 1000;
        }

        .toast.show {
            transform: translateX(0);
        }
    </style>
</head>
<body>
    <div class="page active" id="page1">
        <div class="container">
            <div class="header">
                <button class="back-btn" onclick="goToPage(3)">←</button> <button class="customize-btn">⚙️ Customize</button>
            </div>

            <div class="app-header">
                <div class="app-info">
                    <div class="app-icon">📱</div>
                    <div class="app-details">
                        <h1>ContentCraft AI</h1>
                        <p>Generate engaging social media content in seconds</p>
                    </div>
                </div>
                <div class="plan-info">
                    <div class="plan-text">
                        Free Plan<br>
                        <span id="postsRemaining">3 posts remaining today</span>
                    </div>
                    <button class="upgrade-btn" onclick="showUpgradeModal()">Upgrade to Pro</button>
                </div>
            </div>

            <div class="main-content">
                <div class="section-title">
                    🎯 Create Your Content
                </div>

                <div class="input-group">
                    <label class="input-label">What's your topic?</label>
                    <input type="text" class="topic-input" id="topicInput" placeholder="e.g., morning routines, productivity tips, healthy recipes">
                </div>

                <div class="input-group">
                    <label class="input-label">Choose Platform</label>
                    <div class="options-grid">
                        <button class="option-btn" data-platform="instagram">
                            📷 Instagram
                        </button>
                        <button class="option-btn" data-platform="twitter">
                            🐦 Twitter/X
                        </button>
                        <button class="option-btn" data-platform="linkedin">
                            💼 LinkedIn
                        </button>
                        <button class="option-btn" data-platform="facebook">
                            📘 Facebook
                        </button>
                        <button class="option-btn tiktok-btn" data-platform="tiktok">
                            🎵 TikTok
                        </button>
                    </div>
                </div>

                <div class="input-group">
                    <label class="input-label">Select Tone</label>
                    <div class="tone-grid">
                        <button class="tone-btn" data-tone="engaging">
                            🎯<br>Engaging
                        </button>
                        <button class="tone-btn" data-tone="professional">
                            💼<br>Professional
                        </button>
                        <button class="tone-btn" data-tone="funny">
                            😄<br>Funny
                        </button>
                        <button class="tone-btn" data-tone="inspirational">
                            ✨<br>Inspirational
                        </button>
                        <button class="tone-btn" data-tone="casual">
                            😊<br>Casual
                        </button>
                        <button class="tone-btn" data-tone="educational">
                            🎓<br>Educational
                        </button>
                    </div>
                </div>

                <button class="generate-btn" onclick="showContentTypePage()">
                    <span class="loading" id="loadingSpinner"></span>
                    ⚡ Generate Content
                </button>
            </div>
        </div>
    </div>

    <div class="page" id="page2">
        <div class="container">
            <div class="header">
                <button class="back-btn" onclick="goToPage(1)">←</button>
                <button class="customize-btn">⚙️ Customize</button>
            </div>

            <div class="main-content">
                <div class="section-title">Content Type</div>
                
                <div class="content-type-grid">
                    <button class="content-type-btn selected" data-type="post">
                        📝 Regular Post
                    </button>
                    <button class="content-type-btn" data-type="story">
                        📱 Story
                    </button>
                    <button class="content-type-btn" data-type="caption">
                        💭 Caption
                    </button>
                    <button class="content-type-btn" data-type="thread">
                        🧵 Thread
                    </button>
                    <button class="content-type-btn hashtags-only" data-type="hashtags">
                        # Hashtags
                    </button>
                </div>

                <button class="generate-btn" onclick="generateContent()">
                    <span class="loading" id="loadingSpinner2"></span>
                    ⚡ Generate Content
                </button>
            </div>

            <div class="content-display" id="contentDisplay">
                <div class="placeholder">
                    <div class="target-icon">
                        <div class="arrow"></div>
                    </div>
                    <p>Your generated content will appear here</p>
                    <p style="opacity: 0.6; font-size: 14px; margin-top: 8px;">Enter a topic and hit generate to get started!</p>
                </div>
            </div>
        </div>
    </div>

    <div class="page" id="page3">
        <div class="container">
            <div class="header">
                <button class="back-btn" onclick="goToPage(1)">←</button> <button class="customize-btn">⚙️ Customize</button>
            </div>

            <div class="content-display" id="contentDisplay3">
                <div class="placeholder">
                    <div class="target-icon">
                        <div class="arrow"></div>
                    </div>
                    <p>Your generated content will appear here</p>
                    <p style="opacity: 0.6; font-size: 14px; margin-top: 8px;">Enter a topic and hit generate to get started!</p>
                </div>
            </div>

            <div class="features-section">
                <div class="features-title">Why Choose ContentCraft AI?</div>
                
                <div class="feature-card">
                    <div class="feature-icon">⚡</div>
                    <div class="feature-title">Lightning Fast</div>
                    <div class="feature-description">Generate engaging content in seconds, not hours</div>
                </div>

                <div class="feature-card">
                    <div class="feature-icon">🎯</div>
                    <div class="feature-title">Platform Optimized</div>
                    <div class="feature-description">Content tailored for each social media platform</div>
                </div>

                <div class="feature-card">
                    <div class="feature-icon">🚀</div>
                    <div class="feature-title">Boost Engagement</div>
                    <div class="feature-description">AI-powered content that drives likes, shares
