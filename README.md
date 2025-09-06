<!doctype html>

<html lang="id">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Happy Birthday Radittt 🎉</title>
  <style>
    :root{
      --bg:#FFEEF8;
      --card:#ffffff;
      --accent:#FF6BA7;
      --muted:#6b7280;
    }
    *{box-sizing:border-box}
    body{
      margin:0;min-height:100vh;display:flex;align-items:center;justify-content:center;
      font-family:Inter, system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', Arial;
      background: linear-gradient(180deg,var(--bg) 0%, #FFF8ED 100%);
      padding:24px;
    }
    .card{
      width:100%;max-width:820px;background:var(--card);border-radius:18px;padding:28px;box-shadow:0 10px 30px rgba(15,23,42,0.12);position:relative;overflow:hidden;
    }
    .top-graphic{display:flex;gap:20px;align-items:center}
    .cake{
      width:140px;height:140px;border-radius:18px;background:linear-gradient(180deg,#FFE6F2,#FFD6EC);display:flex;align-items:center;justify-content:center;position:relative;flex-shrink:0;box-shadow:0 8px 20px rgba(255,107,167,0.14);
    }
    .cake:before{content:"";position:absolute;left:18px;right:18px;top:22px;height:60px;background:linear-gradient(90deg,#FFF 0,#FFEAF4 100%);border-radius:10px}
    .flame{position:absolute;top:8px;width:20px;height:34px;border-radius:50% 50% 50% 50%/60% 60% 40% 40%;filter:drop-shadow(0 6px 8px rgba(255,140,0,0.12));transform-origin:center;animation:flicker 950ms infinite}
    .flame:before{content:"";display:block;width:100%;height:100%;background:radial-gradient(circle at 30% 20%, #fff0 0,#ffd27a 30%, #ff8c00 60%, #ff4c00 100%);border-radius:inherit}
    @keyframes flicker{0%{transform:translateY(0) scale(1)}50%{transform:translateY(-2px) scale(1.03)}100%{transform:translateY(0) scale(1)}}
    h1{font-size:34px;margin:0;color:#111827}
    p.lead{margin:14px 0 0;color:var(--muted);font-size:17px}
    .message{margin-top:22px;padding:18px;border-radius:12px;background:linear-gradient(180deg,#FFF0F8,#FFF6FB);font-weight:600;color:#111827;font-size:20px}
    .emoji{margin-left:8px}
    .actions{display:flex;gap:12px;margin-top:20px}
    button{cursor:pointer;border:0;padding:12px 18px;border-radius:12px;font-weight:700;font-size:15px}
    .btn-primary{background:linear-gradient(90deg,var(--accent),#FF9ACB);color:#fff;box-shadow:0 8px 20px rgba(255,107,167,0.12)}
    .btn-ghost{background:transparent;border:2px solid #FFE0EF;color:var(--accent)}
    /* confetti */
    .confetti-piece{position:absolute;width:10px;height:14px;opacity:0;transform-origin:center;pointer-events:none}
    /* second screen */
    .second{display:none;align-items:center;justify-content:center;flex-direction:column;text-align:center;padding:28px}
    .from{font-size:22px;font-weight:800;color:#111827}
    .subtitle{color:var(--muted);margin-top:6px}
    /* responsive */
    @media (max-width:640px){.top-graphic{flex-direction:column;gap:12px}.cake{width:120px;height:120px}}
  </style>
</head>
<body>
  <div class="card" id="card">
    <div class="top-graphic">
      <div class="cake" aria-hidden>
        <div class="flame" style="left:calc(50% - 10px)"></div>
      </div>
      <div style="flex:1">
        <h1>Happy Birthday, Radittt! 🎉</h1>
        <p class="lead">Semoga hari ini penuh gelak tawa😹.</p>
        <div class="message" id="message">hbd radittt semoga TDK jadi kachung<span class="emoji">😹</span></div>
        <div class="actions">
          <button class="btn-primary" id="nextBtn">Selanjutnya</button>
          <button class="btn-ghost" id="restart" style="display:none">Ulangi</button>
        </div>
      </div>
    </div><div class="second" id="second">
  <div style="font-size:70px;line-height:1">🎂</div>
  <div class="from">dari alwizz L lawliet</div>
  <div class="subtitle">hbd radit dewasa🤭</div>
</div>

<!-- confetti container (JS will create pieces) -->

  </div>  <script>
    const nextBtn = document.getElementById('nextBtn');
    const card = document.getElementById('card');
    const message = document.getElementById('message');
    const second = document.getElementById('second');
    const restart = document.getElementById('restart');

    function createConfetti(){
      const colors = ['#FF577F','#FFD166','#8BD3DD','#A78BFA','#FF9ACB'];
      for(let i=0;i<36;i++){
        const el = document.createElement('div');
        el.className='confetti-piece';
        const w = 8 + Math.random()*12;
        el.style.width = w+'px';
        el.style.height = (w*1.4)+'px';
        el.style.background = colors[Math.floor(Math.random()*colors.length)];
        el.style.left = (10 + Math.random()*80)+'%';
        el.style.top = '-10%';
        el.style.transform = `rotate(${Math.random()*360}deg)`;
        card.appendChild(el);
        // animate
        const fallDuration = 2000 + Math.random()*2200;
        el.animate([
          { transform: `translateY(0) rotate(${Math.random()*360}deg)`, opacity:1 },
          { transform: `translateY(${120 + Math.random()*60}vh) rotate(${Math.random()*720}deg)`, opacity:0 }
        ],{duration:fallDuration, easing:'cubic-bezier(.2,.8,.2,1)'});
        // fade out after
        setTimeout(()=> el.remove(), fallDuration+50);
      }
    }

    nextBtn.addEventListener('click',()=>{
      // small reveal animation
      message.animate([{transform:'translateY(0)'},{transform:'translateY(-6px)'},{transform:'translateY(0)'}],{duration:420,iterations:1});
      setTimeout(()=>{
        // show second screen
        document.querySelector('.top-graphic').style.display='none';
        second.style.display='flex';
        restart.style.display='inline-block';
        createConfetti();
      },250);
    });

    restart.addEventListener('click',()=>{
      // reset
      document.querySelector('.top-graphic').style.display='flex';
      second.style.display='none';
      restart.style.display='none';
      createConfetti();
    });

    // accessible: allow Enter key to activate button when focused
    nextBtn.addEventListener('keyup',(e)=>{ if(e.key==='Enter') nextBtn.click(); });
    restart.addEventListener('keyup',(e)=>{ if(e.key==='Enter') restart.click(); });

    // gentle entrance animation
    window.requestAnimationFrame(()=>{
      card.style.transform='translateY(-6px)';card.style.transition='transform 420ms ease';
      setTimeout(()=>card.style.transform='none',420);
    });
  </script></body>
</html>
