<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TERMINAL // ACCESS CONTROL</title>
    <style>
        :root {
            --bg-color: #0b0f14;
            --panel-bg: rgba(16, 24, 34, 0.85);
            --slate-blue: #4a6fa5;
            --slate-light: #7097c2;
            --slate-dark: #1e293b;
            --accent-cyan: #38bdf8;
            --error-red: #ef4444;
            --text-main: #e2e8f0;
            --font-mono: 'Courier New', Courier, monospace;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text-main);
            font-family: var(--font-mono);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow-x: hidden;
            background-image: 
                radial-gradient(circle at 50% 50%, rgba(74, 111, 165, 0.1) 0%, transparent 60%),
                linear-gradient(rgba(15, 23, 42, 0.8) 1px, transparent 1px),
                linear-gradient(90deg, rgba(15, 23, 42, 0.8) 1px, transparent 1px);
            background-size: 100% 100%, 30px 30px, 30px 30px;
        }

        .container {
            width: 100%;
            max-width: 700px;
            padding: 20px;
        }

        /* Passcode Card */
        .card {
            background: var(--panel-bg);
            border: 1px solid var(--slate-dark);
            border-top: 3px solid var(--slate-blue);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.7), 0 0 15px rgba(74, 111, 165, 0.2);
            padding: 40px 30px;
            text-align: center;
            backdrop-filter: blur(10px);
            border-radius: 4px;
            transition: all 0.5s ease;
        }

        h1 {
            font-size: 1.2rem;
            letter-spacing: 3px;
            color: var(--slate-light);
            margin-bottom: 25px;
            text-transform: uppercase;
        }

        .input-group {
            position: relative;
            margin-bottom: 20px;
        }

        input[type="password"] {
            width: 100%;
            max-width: 280px;
            background: rgba(11, 15, 20, 0.9);
            border: 1px solid var(--slate-blue);
            color: var(--accent-cyan);
            font-family: var(--font-mono);
            font-size: 1.5rem;
            padding: 12px 15px;
            text-align: center;
            letter-spacing: 8px;
            outline: none;
            transition: all 0.3s;
            border-radius: 2px;
        }

        input[type="password"]:focus {
            border-color: var(--accent-cyan);
            box-shadow: 0 0 12px rgba(56, 189, 248, 0.3);
        }

        button {
            background: var(--slate-dark);
            color: var(--slate-light);
            border: 1px solid var(--slate-blue);
            padding: 12px 30px;
            font-family: var(--font-mono);
            font-size: 0.9rem;
            letter-spacing: 2px;
            cursor: pointer;
            text-transform: uppercase;
            transition: all 0.3s;
            margin-top: 10px;
        }

        button:hover {
            background: var(--slate-blue);
            color: #fff;
            box-shadow: 0 0 10px rgba(74, 111, 165, 0.5);
        }

        .error-message {
            color: var(--error-red);
            font-size: 0.8rem;
            margin-top: 15px;
            height: 20px;
            letter-spacing: 1px;
        }

        /* Lily Art Display Area */
        .art-container {
            display: none;
            text-align: center;
            opacity: 0;
            transition: opacity 1s ease-in;
        }

        .art-header {
            color: var(--slate-light);
            font-size: 0.8rem;
            letter-spacing: 2px;
            margin-bottom: 15px;
            border-bottom: 1px solid var(--slate-dark);
            padding-bottom: 8px;
        }

        pre#lily-art {
            font-family: monospace;
            font-size: 11px;
            line-height: 1.15;
            color: var(--slate-light);
            text-shadow: 0 0 5px rgba(112, 151, 194, 0.4);
            display: inline-block;
            text-align: left;
            white-space: pre;
            user-select: none;
        }

        /* Glitch Animation Effect */
        .glitch {
            animation: shake 0.2s ease-in-out;
        }

        @keyframes shake {
            0%, 100% { transform: translateX(0); }
            20%, 60% { transform: translateX(-8px); }
            40%, 80% { transform: translateX(8px); }
        }
    </style>
</head>
<body>

    <div class="container">
        <!-- Input Section -->
        <div class="card" id="login-card">
            <h1>AUTHENTICATION REQUIRED</h1>
            <div class="input-group">
                <input type="password" id="passcode" maxlength="6" placeholder="******" autocomplete="off">
            </div>
            <button onclick="checkPasscode()">ENTER</button>
            <div class="error-message" id="error-msg"></div>
        </div>

        <!-- ASCII Lily Output Section -->
        <div class="art-container" id="art-card">
            <div class="art-header">// ACCESS GRANTED - LILY.SYS LOADED</div>
            <pre id="lily-art"></pre>
        </div>
    </div>

    <script>
        const CORRECT_CODE = "140224";

        // Text/ASCII Art of Lily
        const LILY_ART = `
                       .  :  .
                       \\ | /
                    .-'-.-'-.
                   /   |   \\
                  |    |    |
                  \   / \   /
                 .-'-.   .-'-.
                /     \ /     \
               |       |       |
      .---.    \     / \     /    .---.
     /     \   .-'--'-.-'--'-.   /     \
    |       | /       |       \ |       |
     \     / |        |        | \     /
      '-.-'   \      / \      /   '-.-'
        |      '-.--'   '--.-'      |
        |        /    |    \        |
        |       |     |     |       |
        |        \    |    /        |
        |         '-.-'-.-'         |
        |             |             |
        |             |             |
        \             |             /
         \            |            /
          '--.________|________.--'
                      |
                      |
                     / \
                    /   \
                   /     \
                  /       \
                 /         \
                |    /\     |
                |   /  \    |
                |  /    \   |
                 \/      \/
                      |
                      |
                     ===
        `;

        // Check password on Enter key
        document.getElementById('passcode').addEventListener('keypress', function (e) {
            if (e.key === 'Enter') {
                checkPasscode();
            }
        });

        function checkPasscode() {
            const input = document.getElementById('passcode');
            const errorMsg = document.getElementById('error-msg');
            const loginCard = document.getElementById('login-card');
            const artCard = document.getElementById('art-card');

            if (input.value === CORRECT_CODE) {
                // Fade out login card
                loginCard.style.opacity = '0';
                setTimeout(() => {
                    loginCard.style.display = 'none';
                    artCard.style.display = 'block';
                    setTimeout(() => {
                        artCard.style.opacity = '1';
                        renderArtSlowly();
                    }, 50);
                }, 500);
            } else {
                // Display error and shake effect
                errorMsg.innerText = "ACCESS DENIED: INVALID PASSCODE";
                loginCard.classList.add('glitch');
                input.value = '';
                setTimeout(() => {
                    loginCard.classList.remove('glitch');
                }, 300);
            }
        }

        // Typewriter effect for ASCII Art
        function renderArtSlowly() {
            const artTarget = document.getElementById('lily-art');
            let index = 0;
            artTarget.innerText = '';

            const timer = setInterval(() => {
                if (index < LILY_ART.length) {
                    artTarget.innerText += LILY_ART.charAt(index);
                    index++;
                } else {
                    clearInterval(timer);
                }
            }, 2); // Speed of drawing
        }
    </script>
</body>
</html>