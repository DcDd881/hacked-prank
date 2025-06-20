# hacked-prank<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Security Breach Detected</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Source+Code+Pro&display=swap');

  body {
    margin: 0;
    background: #000;
    color: #0f0;
    font-family: 'Source Code Pro', monospace;
    overflow: hidden;
    display: flex;
    flex-direction: column;
    height: 100vh;
  }

  #terminal {
    flex: 1;
    padding: 20px;
    overflow-y: auto;
    white-space: pre-wrap;
    font-size: 1.2em;
  }

  .warning {
    color: red;
    font-weight: bold;
    animation: flash 1s infinite;
  }

  @keyframes flash {
    0%, 50%, 100% {opacity: 1;}
    25%, 75% {opacity: 0;}
  }

  #progress-container {
    width: 80%;
    background: #222;
    margin: 10px auto;
    border-radius: 5px;
    height: 25px;
    overflow: hidden;
    box-shadow: 0 0 5px #0f0 inset;
  }

  #progress-bar {
    height: 100%;
    width: 0%;
    background: linear-gradient(90deg, #f00, #800);
    transition: width 0.2s ease-in-out;
  }

  #countdown {
    text-align: center;
    font-size: 1.5em;
    color: red;
    font-weight: bold;
    margin: 10px 0;
  }
</style>
</head>
<body>

<div id="terminal"></div>

<div id="progress-container">
  <div id="progress-bar"></div>
</div>

<div id="countdown"></div>

<script>
  const terminal = document.getElementById('terminal');
  const progressBar = document.getElementById('progress-bar');
  const countdown = document.getElementById('countdown');

  const lines = [
    "⚠️ SECURITY BREACH DETECTED",
    "Connecting to external hacker network...",
    "Attempting to override firewall...",
    "Firewall override successful!",
    "Accessing secure files...",
    "Extracting password database...",
    "Uploading files to remote server...",
    "Current IP: 192.168.1.101",
    "Location: Unknown",
    "System integrity compromised!",
    "DISCONNECT IMMEDIATELY TO PREVENT DATA LOSS!",
    "Uploading data in progress...",
  ];

  let lineIndex = 0;
  let progress = 0;
  let countdownValue = 15; // seconds for self-destruct countdown

  function appendLine(text, cls = '') {
    const p = document.createElement('p');
    p.textContent = text;
    if (cls) p.classList.add(cls);
    terminal.appendChild(p);
    terminal.scrollTop = terminal.scrollHeight;
  }

  function showLines() {
    if (lineIndex < lines.length) {
      appendLine(lines[lineIndex], lineIndex === 0 || lineIndex === lines.length - 2 ? 'warning' : '');
      lineIndex++;
      setTimeout(showLines, 1500);
    } else {
      startProgressBar();
    }
  }

  function startProgressBar() {
    if (progress < 100) {
      progress += Math.floor(Math.random() * 7) + 3; // progress 3-9%
      if (progress > 100) progress = 100;
      progressBar.style.width = progress + '%';
      if (progress < 100) {
        setTimeout(startProgressBar, 300);
      } else {
        startCountdown();
      }
    }
  }

  function startCountdown() {
    countdown.textContent = `DISCONNECT NOW! Device will self-destruct in ${countdownValue} seconds.`;
    const timer = setInterval(() => {
      countdownValue--;
      if (countdownValue <= 0) {
        clearInterval(timer);
        countdown.textContent = "💥 DEVICE SELF-DESTRUCTED 💥";
        appendLine("All data wiped from system!", 'warning');
        // Optional: flash screen red rapidly
        flashScreen();
      } else {
        countdown.textContent = `DISCONNECT NOW! Device will self-destruct in ${countdownValue} seconds.`;
      }
    }, 1000);
  }

  function flashScreen() {
    let flashes = 0;
    const flashInterval = setInterval(() => {
      document.body.style.background = flashes % 2 === 0 ? 'red' : 'black';
      flashes++;
      if (flashes > 10) {
        clearInterval(flashInterval);
        document.body.style.background = 'black';
      }
    }, 200);
  }

  // Start the animation
  showLines();

</script>

</body>
</html>
