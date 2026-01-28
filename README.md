# Ayush-and-priyanshi-story
<!doctype html>
<html lang="hi">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Ayush Dubey - One Sided Love</title>
  <style>
    *{box-sizing:border-box}
    body{
      margin:0;
      font-family: system-ui, -apple-system, Segoe UI, Roboto, Arial;
      background: radial-gradient(circle at top, #111 0%, #000 60%);
      color:#fff;
      height:100vh;
      display:flex;
      align-items:center;
      justify-content:center;
      padding:16px;
    }
    .card{
      width:min(560px, 100%);
      background: rgba(255,255,255,0.06);
      border:1px solid rgba(255,255,255,0.12);
      border-radius:20px;
      padding:18px;
      box-shadow: 0 20px 60px rgba(0,0,0,0.5);
    }
    .title{
      font-size:18px;
      opacity:.9;
      margin-bottom:10px;
      display:flex;
      justify-content:space-between;
      gap:10px;
      flex-wrap:wrap;
    }
    .badge{
      font-size:12px;
      padding:6px 10px;
      border-radius:999px;
      background: rgba(255,255,255,0.08);
      border:1px solid rgba(255,255,255,0.10);
    }
    .speaker{
      font-size:14px;
      opacity:.85;
      margin:10px 0 6px;
    }
    .dialogue{
      font-size:18px;
      line-height:1.55;
      padding:14px;
      border-radius:16px;
      background: rgba(0,0,0,0.35);
      border:1px solid rgba(255,255,255,0.08);
      min-height:110px;
      white-space:pre-line;
    }
    .controls{
      display:flex;
      gap:10px;
      margin-top:12px;
      flex-wrap:wrap;
    }
    button{
      flex:1;
      border:none;
      padding:12px 14px;
      border-radius:14px;
      font-size:15px;
      cursor:pointer;
      background: rgba(255,255,255,0.10);
      color:#fff;
      border:1px solid rgba(255,255,255,0.12);
    }
    button:active{transform:scale(.99)}
    .primary{
      background: linear-gradient(135deg, rgba(255,80,120,.9), rgba(120,80,255,.9));
      border:none;
    }
    .small{
      flex:0;
      padding:10px 12px;
      font-size:13px;
      opacity:.95;
    }
    .footer{
      margin-top:10px;
      font-size:12px;
      opacity:.65;
      text-align:center;
    }
  </style>
</head>
<body>
  <div class="card">
    <div class="title">
      <div>💔 <b>Ayush Dubey</b> ki kahani</div>
      <div class="badge">One-Sided Love</div>
    </div>

    <div class="speaker" id="speaker">Narrator (Ayush)</div>
    <div class="dialogue" id="dialogue">Start dabao… main tumhe apni kahani sunata hoon.</div>

    <div class="controls">
      <button class="primary" id="nextBtn">▶ Start / Next</button>
      <button class="small" id="autoBtn">⏯ Auto: OFF</button>
      <button class="small" id="restartBtn">↺ Restart</button>
    </div>

    <div class="footer">Made for: Ayush Dubey × Priyanshi</div>
  </div>

<script>
  // Story: Ayush narrating
  const story = [
    {s:"Narrator (Ayush)", d:"Main Ayush Dubey…\nAur ye meri ek one sided love story hai…"},
    {s:"Narrator (Ayush)", d:"Uska naam Priyanshi hai…\nAur maine usse dil se chaha tha…"},
    {s:"Narrator (Ayush)", d:"Aaj main decide kar chuka tha…\nCall karke seedha propose karunga…"},
    {s:"Narrator (Ayush)", d:"📞 (Phone ringing…)"},
    {s:"Priyanshi", d:"Hello… Ayush?"},
    {s:"Narrator (Ayush)", d:"Mere haath kaanp rahe the…\nPar maine bol diya…"},
    {s:"Ayush", d:"Priyanshi… I love you.\nMain tumse pyaar karta hoon…"},
    {s:"Priyanshi", d:"Ayush… tum ache ho…\nBut mujhe ye sab nahi chahiye…"},
    {s:"Priyanshi", d:"Main tumhe us nazar se nahi dekhti…\nSorry…"},
    {s:"Narrator (Ayush)", d:"Uske ‘Nahi’ bolte hi…\nMera dil toot gaya… 💔"},
    {s:"Ayush", d:"Okay… samajh gaya…"},
    {s:"Narrator (Ayush)", d:"Maine call cut kar diya…\nAur chup chaap chal diya…"},
    {s:"Narrator (Ayush)", d:"Main move on karne ki koshish karta raha…\nPar main kar hi nahi paya…"},
    {s:"Narrator (Ayush)", d:"Raat ko maine message kiya…\nShayad reply aa jaye…"},
    {s:"Ayush (Chat)", d:"Priyanshi… please ek baar baat kar lo…"},
    {s:"System", d:"❌ You can’t send message to this user."},
    {s:"Narrator (Ayush)", d:"Haan…\nUsne mujhe block kar diya…"},
    {s:"Narrator (Ayush)", d:"Aur main…\nUsi raat… raat bhar rota raha… 🌧️😭"},
    {s:"Narrator (Ayush)", d:"💔 ONE SIDED LOVE ENDS HERE\nTHE END"}
  ];

  let i = -1;
  let auto = false;
  let autoTimer = null;

  const speaker = document.getElementById("speaker");
  const dialogue = document.getElementById("dialogue");
  const nextBtn = document.getElementById("nextBtn");
  const autoBtn = document.getElementById("autoBtn");
  const restartBtn = document.getElementById("restartBtn");

  function render() {
    if (i < 0) return;
    speaker.textContent = story[i].s;
    dialogue.textContent = story[i].d;
    if (i === story.length - 1) nextBtn.textContent = "↺ Restart";
    else nextBtn.textContent = "▶ Next";
  }

  function next() {
    if (i === story.length - 1) { restart(); return; }
    i++;
    render();
  }

  function restart() {
    i = -1;
    speaker.textContent = "Narrator (Ayush)";
    dialogue.textContent = "Start dabao… main tumhe apni kahani sunata hoon.";
    nextBtn.textContent = "▶ Start / Next";
  }

  function toggleAuto() {
    auto = !auto;
    autoBtn.textContent = auto ? "⏯ Auto: ON" : "⏯ Auto: OFF";
    if (auto) {
      autoTimer = setInterval(() => {
        if (i === story.length - 1) { toggleAuto(); return; }
        next();
      }, 2600);
    } else {
      clearInterval(autoTimer);
      autoTimer = null;
    }
  }

  nextBtn.addEventListener("click", next);
  autoBtn.addEventListener("click", toggleAuto);
  restartBtn.addEventListener("click", restart);
</script>
</body>
</html>
