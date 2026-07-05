# emiu
OK
<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<title>Cho em 💌</title>
<style>
  :root {
    --cream: #FFF6EF;
    --box-pink: #FFC7DC;
    --box-pink-dark: #FF9FC2;
    --ribbon: #FFE066;
    --mint: #BFEFDD;
    --lavender: #DCCBFF;
    --plum: #6B4A5C;
    --plum-soft: #9C7C8C;
  }

  * { box-sizing: border-box; -webkit-tap-highlight-color: transparent; }

  html, body {
    margin: 0;
    height: 100%;
    background: var(--cream);
    font-family: -apple-system, "Segoe UI", Roboto, sans-serif;
    overflow: hidden;
  }

  body {
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
  }

  /* Nền lấp lánh trôi nổi */
  .bg-doodles {
    position: absolute;
    inset: 0;
    overflow: hidden;
    pointer-events: none;
  }

  .doodle {
    position: absolute;
    font-size: 22px;
    opacity: 0.35;
    animation: float linear infinite;
  }

  @keyframes float {
    from { transform: translateY(110vh) rotate(0deg); }
    to { transform: translateY(-15vh) rotate(360deg); }
  }

  .stage {
    width: 100%;
    max-width: 420px;
    height: 100%;
    max-height: 820px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 32px 24px;
    position: relative;
    text-align: center;
  }

  .eyebrow {
    color: var(--plum-soft);
    font-size: 13px;
    letter-spacing: 3px;
    text-transform: uppercase;
    margin-bottom: 6px;
  }

  .headline {
    font-family: "Bradley Hand", "Segoe Script", cursive;
    color: var(--plum);
    font-size: 34px;
    margin: 0 0 30px;
    transform: rotate(-1deg);
  }

  /* Hộp quà */
  .gift {
    position: relative;
    width: 150px;
    height: 130px;
    cursor: pointer;
    margin-bottom: 26px;
    transition: transform 0.2s ease;
  }

  .gift:active { transform: scale(0.95); }

  .gift.opened { pointer-events: none; }

  .lid {
    position: absolute;
    top: 0;
    left: -6px;
    right: -6px;
    height: 42px;
    background: var(--box-pink-dark);
    border-radius: 10px 10px 4px 4px;
    box-shadow: 0 4px 0 rgba(0,0,0,0.06);
    transition: transform 0.5s cubic-bezier(.34,1.56,.64,1), opacity 0.4s ease;
    transform-origin: center bottom;
    z-index: 3;
  }

  .gift.opened .lid {
    transform: translateY(-70px) rotate(-18deg);
    opacity: 0;
  }

  .base {
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    height: 96px;
    background: var(--box-pink);
    border-radius: 4px 4px 12px 12px;
    box-shadow: 0 6px 0 rgba(0,0,0,0.06);
    z-index: 1;
  }

  .ribbon-v {
    position: absolute;
    top: 0;
    bottom: 0;
    left: 50%;
    width: 18px;
    margin-left: -9px;
    background: var(--ribbon);
    z-index: 2;
  }

  .ribbon-h {
    position: absolute;
    left: 0;
    right: 0;
    top: 40px;
    height: 18px;
    background: var(--ribbon);
    z-index: 2;
  }

  .bow {
    position: absolute;
    top: -14px;
    left: 50%;
    transform: translateX(-50%);
    font-size: 30px;
    z-index: 4;
    transition: transform 0.4s ease, opacity 0.4s ease;
  }

  .gift.opened .bow {
    transform: translateX(-50%) translateY(-80px) scale(0.6) rotate(20deg);
    opacity: 0;
  }

  .hint {
    color: var(--plum-soft);
    font-size: 14px;
    margin-bottom: 4px;
    animation: pulseHint 1.6s ease-in-out infinite;
  }

  @keyframes pulseHint {
    0%, 100% { opacity: 0.55; }
    50% { opacity: 1; }
  }

  .gift.opened + .hint { display: none; }

  /* Nhân vật bật ra */
  .mascot {
    position: absolute;
    left: 50%;
    bottom: 40px;
    width: 84px;
    height: 84px;
    margin-left: -42px;
    z-index: 5;
    opacity: 0;
    transform: translateY(10px) scale(0.4);
    transition: opacity 0.35s ease 0.25s, transform 0.45s cubic-bezier(.34,1.56,.64,1) 0.25s;
  }

  .gift.opened .mascot {
    opacity: 1;
    transform: translateY(-96px) scale(1);
  }

  .mascot.bounce { animation: bounce 0.7s ease-in-out infinite 0.7s; }

  @keyframes bounce {
    0%, 100% { transform: translateY(-96px) scale(1); }
    50% { transform: translateY(-106px) scale(1); }
  }

  /* Khu vực lời nhắn */
  .message-card {
    width: 100%;
    background: #ffffff;
    border-radius: 22px;
    padding: 22px 20px;
    box-shadow: 0 10px 30px rgba(107,74,92,0.12);
    opacity: 0;
    transform: translateY(14px);
    transition: opacity 0.4s ease 0.5s, transform 0.4s ease 0.5s;
    min-height: 96px;
  }

  .message-card.show {
    opacity: 1;
    transform: translateY(0);
  }

  .message-text {
    font-family: "Bradley Hand", "Segoe Script", cursive;
    color: var(--plum);
    font-size: 21px;
    line-height: 1.5;
    min-height: 1.6em;
  }

  .cursor {
    display: inline-block;
    width: 2px;
    background: var(--plum);
    margin-left: 2px;
    animation: blink 0.8s step-end infinite;
  }

  @keyframes blink { 50% { opacity: 0; } }

  .again {
    margin-top: 16px;
    border: none;
    background: var(--lavender);
    color: var(--plum);
    padding: 10px 20px;
    border-radius: 999px;
    font-size: 13px;
    font-weight: 600;
    opacity: 0;
    transition: opacity 0.4s ease;
    cursor: pointer;
  }

  .again.show { opacity: 1; }

  /* Confetti tim bay khi mở quà */
  .burst {
    position: absolute;
    left: 50%;
    bottom: 90px;
    width: 0;
    height: 0;
    z-index: 6;
    pointer-events: none;
  }

  .burst span {
    position: absolute;
    font-size: 20px;
    opacity: 0;
  }

  .burst.go span {
    animation: heartUp 1.1s ease-out forwards;
  }

  @keyframes heartUp {
    0% { opacity: 1; transform: translate(0,0) scale(0.6) rotate(0deg); }
    100% { opacity: 0; transform: translate(var(--dx), var(--dy)) scale(1.1) rotate(var(--rot)); }
  }
</style>
</head>
<body>

<div class="bg-doodles" id="bgDoodles"></div>

<div class="stage">
  <div class="eyebrow">Có 1 tin nhắn cho em</div>
  <h1 class="headline">Mở ra xem nào 👀</h1>

  <div class="gift" id="gift">
    <div class="bow">🎀</div>
    <div class="lid" id="lid"></div>
    <div class="ribbon-v"></div>
    <div class="ribbon-h"></div>
    <div class="base"></div>

    <svg class="mascot" id="mascot" viewBox="0 0 100 100">
      <circle cx="50" cy="55" r="30" fill="#FFE3C2"/>
      <circle cx="30" cy="42" r="9" fill="#FFE3C2"/>
      <circle cx="70" cy="42" r="9" fill="#FFE3C2"/>
      <circle cx="30" cy="42" r="5" fill="#FF9FC2"/>
      <circle cx="70" cy="42" r="5" fill="#FF9FC2"/>
      <path d="M35 50 Q35 46 39 46 Q43 46 43 50 Q43 54 39 56 Q35 54 35 50 Z" fill="#6B4A5C"/>
      <path d="M57 50 Q57 46 61 46 Q65 46 65 50 Q65 54 61 56 Q57 54 57 50 Z" fill="#6B4A5C"/>
      <circle cx="34" cy="62" r="5" fill="#FFC7DC" opacity="0.8"/>
      <circle cx="66" cy="62" r="5" fill="#FFC7DC" opacity="0.8"/>
      <path d="M40 64 Q50 72 60 64" stroke="#6B4A5C" stroke-width="2.5" fill="none" stroke-linecap="round"/>
    </svg>

    <div class="burst" id="burst"></div>
  </div>

  <div class="hint" id="hint">Chạm vào hộp quà 🎁</div>

  <div class="message-card" id="messageCard">
    <div class="message-text" id="messageText"><span class="cursor"></span></div>
  </div>

  <button class="again" id="againBtn">Mở lại 🔁</button>
</div>

<script>
  /* ====== BẠN CÓ THỂ SỬA Ở ĐÂY ====== */
  const HER_NAME = "em"; // đổi thành tên bạn gái, ví dụ "Mèo con"
  const LINES = [
    `Này ${HER_NAME} ơi...`,
    `Hôm nay anh chẳng có lý do gì đặc biệt cả 🙈`,
    `Chỉ là tự nhiên rất nhớ ${HER_NAME} thôi.`,
    `Nhớ đến mức phải làm cả 1 cái hộp quà ảo thế này 😌`,
    `Cảm ơn ${HER_NAME} vì đã xuất hiện trong đời anh nha 💛`,
    `Yêu ${HER_NAME} nhiều lắm đó~ 💌`
  ];
  /* =================================== */

  const gift = document.getElementById('gift');
  const messageCard = document.getElementById('messageCard');
  const messageText = document.getElementById('messageText');
  const againBtn = document.getElementById('againBtn');
  const burst = document.getElementById('burst');
  const mascot = document.getElementById('mascot');

  const bgDoodles = document.getElementById('bgDoodles');
  const doodleChars = ['💗','✨','💫','🩷'];
  for (let i = 0; i < 14; i++) {
    const d = document.createElement('div');
    d.className = 'doodle';
    d.textContent = doodleChars[i % doodleChars.length];
    d.style.left = `${Math.random() * 100}%`;
    d.style.animationDuration = `${8 + Math.random() * 8}s`;
    d.style.animationDelay = `${Math.random() * 8}s`;
    bgDoodles.appendChild(d);
  }

  function spawnHearts() {
    burst.innerHTML = '';
    const emojis = ['💗','💛','✨','🩷'];
    for (let i = 0; i < 10; i++) {
      const s = document.createElement('span');
      s.textContent = emojis[i % emojis.length];
      const dx = (Math.random() - 0.5) * 140;
      const dy = -(90 + Math.random() * 90);
      s.style.setProperty('--dx', `${dx}px`);
      s.style.setProperty('--dy', `${dy}px`);
      s.style.setProperty('--rot', `${(Math.random() - 0.5) * 90}deg`);
      s.style.left = `${(Math.random() - 0.5) * 20}px`;
      s.style.animationDelay = `${Math.random() * 0.25}s`;
      burst.appendChild(s);
    }
    burst.classList.remove('go');
    void burst.offsetWidth;
    burst.classList.add('go');
  }

  let typing = false;

  function typeLines() {
    if (typing) return;
    typing = true;
    messageCard.classList.add('show');
    messageText.innerHTML = '<span class="cursor"></span>';
    let full = LINES.join('\n');
    let i = 0;
    const cursor = messageText.querySelector('.cursor');

    function step() {
      if (i <= full.length) {
        messageText.textContent = full.slice(0, i);
        messageText.appendChild(cursor);
        i++;
        setTimeout(step, 32);
      } else {
        typing = false;
        againBtn.classList.add('show');
      }
    }
    step();
  }

  function openGift() {
    if (gift.classList.contains('opened')) return;
    gift.classList.add('opened');
    mascot.classList.add('bounce');
    spawnHearts();
    setTimeout(typeLines, 550);
  }

  function resetCard() {
    gift.classList.remove('opened');
    mascot.classList.remove('bounce');
    messageCard.classList.remove('show');
    againBtn.classList.remove('show');
    messageText.innerHTML = '<span class="cursor"></span>';
  }

  gift.addEventListener('click', openGift);
  againBtn.addEventListener('click', () => {
    resetCard();
    setTimeout(openGift, 350);
  });
</script>

</body>
</html>
