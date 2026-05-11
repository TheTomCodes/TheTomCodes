<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Live UI Demo - Working Proof</title>
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; font-family: system-ui, 'Segoe UI', sans-serif; }
    body { background: linear-gradient(145deg, #0a0f1e, #03050b); min-height: 100vh; display: flex; justify-content: center; align-items: center; padding: 1rem; }
    .card { background: rgba(20, 25, 45, 0.7); backdrop-filter: blur(12px); border-radius: 2rem; padding: 2rem; width: 500px; max-width: 100%; border: 1px solid #7c3aed; box-shadow: 0 25px 40px -12px black; }
    h1 { background: linear-gradient(135deg, #c084fc, #60a5fa); -webkit-background-clip: text; background-clip: text; color: transparent; margin-bottom: 1rem; }
    button { background: #7c3aed; border: none; padding: 0.6rem 1.2rem; border-radius: 2rem; font-weight: bold; color: white; cursor: pointer; transition: 0.2s; margin-top: 1rem; }
    button:hover { background: #a855f7; transform: scale(1.02); box-shadow: 0 0 12px #a855f7; }
    .value { font-size: 3rem; font-weight: 800; color: #c084fc; margin: 1rem 0; }
    .time { font-family: monospace; background: #00000040; padding: 0.5rem; border-radius: 1rem; text-align: center; margin-top: 1rem; }
    input { width: 100%; padding: 0.7rem; border-radius: 1rem; border: 1px solid #2d3250; background: #0f1222; color: white; margin: 0.5rem 0; }
  </style>
</head>
<body>
<div class="card">
  <h1>✨ Advanced UI Preview</h1>
  <p>This runs 100% — live counter, clock, and editable preview</p>
  <div class="value" id="counter">0</div>
  <button id="incBtn">Increase +1</button>
  <button id="resetBtn" style="background: #334155;">Reset</button>

  <input type="text" id="textInput" placeholder="Type something..." value="Hello world">
  <div style="background: #00000030; border-radius: 1rem; padding: 0.5rem; margin-top: 0.5rem;">
    Live preview: <strong id="preview">Hello world</strong>
  </div>

  <div class="time" id="liveClock">--:--:--</div>
</div>
<script>
  // fully functional interactive components
  let count = 0;
  const counterDiv = document.getElementById('counter');
  const incBtn = document.getElementById('incBtn');
  const resetBtn = document.getElementById('resetBtn');
  incBtn.onclick = () => { count++; counterDiv.innerText = count; };
  resetBtn.onclick = () => { count = 0; counterDiv.innerText = count; };

  const textInput = document.getElementById('textInput');
  const previewSpan = document.getElementById('preview');
  textInput.oninput = () => { previewSpan.innerText = textInput.value; };

  function updateClock() {
    const now = new Date();
    document.getElementById('liveClock').innerText = now.toLocaleTimeString();
  }
  setInterval(updateClock, 1000);
  updateClock();
</script>
</body>
</html>
