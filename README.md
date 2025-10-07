<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8">
  <title>Геймификация – Блок streak и задания VK Игры</title>
  <style>
    body {
      background: #f4f7fa;
      font-family: 'VK Sans', Arial, sans-serif;
      margin: 0;
    }
    .gamification-block-vk {
      margin: 40px auto;
      background: #fff;
      border-radius: 16px;
      box-shadow: 0 4px 16px rgba(0,0,0,0.07);
      max-width: 640px;
      padding: 38px 36px 24px 36px;
    }
    .vk-header {
      display: flex;
      align-items: center;
      justify-content: space-between;
      margin-bottom: 14px;
    }
    .vk-title {
      font-size: 1.4em;
      font-weight: 700;
      color: #2666a3;
    }
    .vk-coins {
      background: linear-gradient(90deg, #70bcf8, #45bef6 70%);
      color: #fff;
      font-size: 1.08em;
      font-weight: 700;
      border-radius: 8px;
      padding: 7px 20px;
      box-shadow: 0 2px 8px rgba(52,159,253,0.08);
      display: flex;
      align-items: center;
      gap: 8px;
    }
    .vk-coins-emoji {
      font-size: 1.18em;
    }
    .progressbar-section {
      margin-bottom: 22px;
    }
    .progressbar-labels {
      display: flex;
      align-items: center;
      justify-content: space-between;
      margin-bottom: 6px;
    }
    .progressbar-current-streak {
      font-size: 1.18em;
      color: #1570be;
      font-weight: 700;
      background: #f0f7ff;
      border-radius: 7px;
      padding: 5px 14px;
    }
    .progressbar-days-text {
      color: #5f6c7e;
      font-size: 1.02em;
    }
    .vk-progressbar {
      display: flex;
      align-items: center;
      gap: 10px;
      margin-bottom: 0;
    }
    .bar-bg {
      flex: 1;
      height: 20px;
      background: #ddefff;
      border-radius: 10px;
      position: relative;
      margin-right: 0;
    }
    .bar-fill {
      background: linear-gradient(90deg, #347cfd 30%, #38b6fa 100%);
      height: 100%;
      border-radius: 10px;
      width: 65%; /* подправь под текущую серию */
      position: relative;
      box-shadow: 0 6px 24px rgba(80,160,255,0.15);
      transition: width 0.4s;
    }
    .bar-marks-below {
      display: flex;
      justify-content: space-between;
      align-items: flex-start;
      margin-top: 7px;
      margin-left: 2px;
      margin-right: 6px;
    }
    .mark-below {
      display: flex;
      flex-direction: column;
      align-items: center;
      font-size: 0.96em;
      min-width: 32px;
    }
    .mark-dot-below {
      width: 8px;
      height: 8px;
      border-radius: 50%;
      background: #38b6fa;
      margin-bottom: 3px;
      box-shadow: 0 0 0 2px #fff;
      margin-top: 2px;
    }
    .mark-prize-below {
      background: #45bef6;
      color: #fff;
      font-size: 0.94em;
      padding: 2px 6px;
      border-radius: 5px;
      margin-top: 2px;
      box-shadow: 0 2px 4px rgba(70,190,246,0.13);
    }
    /* Tasks */
    .tasks-section-vk {
      margin-bottom: 18px;
    }
    .tasks-title-vk {
      font-weight: 700;
      font-size: 1.13em;
      color: #1570be;
      margin-bottom: 8px;
    }
    .task-list-vk {
      list-style: none;
      margin: 0;
      padding: 0;
      display: flex;
      flex-wrap: wrap;
      gap: 12px;
    }
    .task-card-vk {
      flex: 1;
      min-width: 170px;
      max-width: 220px;
      background: #e6f3ff;
      border-radius: 8px;
      padding: 10px 16px;
      display: flex;
      flex-direction: column;
      align-items: flex-start;
    }
    .task-title-vk {
      font-weight: 500;
      margin-bottom: 6px;
      color: #2666a3;
    }
    .task-reward-vk {
      font-size: 0.97em;
      color: #45bef6;
      margin-bottom: 6px;
    }
    .task-action-vk {
      background: #38b6fa;
      color: #fff;
      border: none;
      border-radius: 5px;
      padding: 5px 13px;
      font-size: 0.97em;
      cursor: pointer;
      margin-top: 2px;
    }
    /* Raffle */
    .raffle-block {
      margin-top: 22px;
      display: flex;
      align-items: center;
      gap: 18px;
    }
    .raffle-desc {
      color: #45bef6;
      font-weight: 500;
      font-size: 1.09em;
      background: #f0f7ff;
      border-radius: 8px;
      padding: 6px 14px;
    }
    .raffle-btn {
      background: linear-gradient(90deg, #45bef6 60%, #7fbcff 100%);
      color: #fff;
      border: none;
      border-radius: 7px;
      font-size: 1.08em;
      padding: 11px 25px;
      font-weight: 700;
      box-shadow: 0 2px 8px rgba(70,190,246,0.14);
      cursor: pointer;
    }
  </style>
</head>
<body>
  <div class="gamification-block-vk">
    <div class="vk-header">
      <div class="vk-title">Твой прогресс</div>
      <div class="vk-coins">
        <span class="vk-coins-emoji">💎</span> <span>72 кристалла</span>
      </div>
    </div>
    <div class="progressbar-section">
      <div class="progressbar-labels">
        <span class="progressbar-days-text">Твой прогресс</span>
        <span class="progressbar-current-streak">5 дней подряд</span>
      </div>
      <div class="vk-progressbar">
        <div class="bar-bg">
          <div class="bar-fill"></div>
        </div>
      </div>
      <div class="bar-marks-below">
        <span class="mark-below"><span class="mark-dot-below"></span>1<br><span class="mark-prize-below">+3</span></span>
        <span class="mark-below"><span class="mark-dot-below"></span>3<br><span class="mark-prize-below">+6</span></span>
        <span class="mark-below"><span class="mark-dot-below"></span>5<br><span class="mark-prize-below">+12</span></span>
        <span class="mark-below"><span class="mark-dot-below"></span>7<br><span class="mark-prize-below">+20</span></span>
      </div>
    </div>
    <div class="tasks-section-vk">
      <div class="tasks-title-vk">Задания за кристаллы</div>
      <ul class="task-list-vk">
        <li class="task-card-vk">
          <div class="task-title-vk">Поиграй в любую игру</div>
          <div class="task-reward-vk">+5 монет</div>
          <button class="task-action-vk">Выполнить</button>
        </li>
        <li class="task-card-vk">
          <div class="task-title-vk">Добавь игру в избранное</div>
          <div class="task-reward-vk">+3 кристалла</div>
          <button class="task-action-vk">Выполнить</button>
        </li>
        <li class="task-card-vk">
          <div class="task-title-vk">Поделись игрой с другом</div>
          <div class="task-reward-vk">+4 кристалла</div>
          <button class="task-action-vk">Выполнить</button>
        </li>
      </ul>
    </div>
    <div class="raffle-block">
      <div class="raffle-desc">
        Используй свои кристаллы для участия в розыгрыше призов!
      </div>
      <button class="raffle-btn">Участвовать за 10 кристаллов</button>
    </div>
  </div>
</body>
</html>
<!-- Кристалл всплывающий + Колесо фортуны + скрипт -->
<div id="crystal-popup" style="display:none;position:fixed;left:50%;top:56%;transform:translate(-50%,-50%);z-index:999;">
  <div style="font-size:70px;animation:crystal-float 1.2s ease-out;">💎</div>
</div>
<div id="fortune-modal" style="display:none;position:fixed;left:50%;top:50%;transform:translate(-50%,-50%);background:#fff;border-radius:16px;box-shadow:0 8px 32px #347cfd1e;padding:30px 40px;z-index:998;text-align:center;min-width:235px;min-height:216px;position:relative;">
  <div id="wheel-container" style="width:180px;height:180px;margin:0 auto 20px;position:relative;">
    <!-- Статичная стрелка ЗА ПРЕДЕЛАМИ колеса, указывает НА него -->
    <div style="position:absolute;top:-16px;left:50%;transform:translateX(-50%);width:0;height:0;border-left:10px solid transparent;border-right:10px solid transparent;border-top:20px solid #5d5fef;z-index:15;"></div>
    
    <!-- Крутящееся колесо -->
    <div id="wheel-svg" style="width:100%;height:100%;border-radius:50%;position:relative;transition:transform 3s cubic-bezier(.17,.67,.83,.67);background:conic-gradient(from 0deg, #45bef6 0deg 60deg, #70bcf8 60deg 120deg, #38b6fa 120deg 180deg, #7fbcff 180deg 240deg, #45bef6 240deg 300deg, #347cfd 300deg 360deg);border:4px solid #2666a3;box-shadow:0 4px 16px #347cfd22;">
      <div style="position:absolute;top:50%;left:50%;transform:translate(-50%,-50%);width:20px;height:20px;background:#2666a3;border-radius:50%;z-index:10;"></div>
    </div>
  </div>
  <div id="fortune-result" style="font-size:1.15em;margin-top:15px;color:#2666a3;min-height:24px;"></div>
  <button class="raffle-btn" onclick="closeWheel()" style="margin-top:15px;">Закрыть</button>
</div>
<style>
@keyframes crystal-float {
  0% {transform:scale(0) translateY(0px);opacity:0;}
  30% {transform:scale(1.3) translateY(-20px);opacity:1;}
  60% {transform:scale(1) translateY(-30px);opacity:1;}
  100% {transform:scale(0.8) translateY(-60px);opacity:0;}
}
</style>
<script>
// Добавляем крестик в главный блок макета
document.addEventListener('DOMContentLoaded', function() {
  const mainBlock = document.querySelector('.gamification-block-vk');
  if (mainBlock) {
    const closeBtn = document.createElement('div');
    closeBtn.style.cssText = 'position:absolute;top:12px;right:12px;width:24px;height:24px;background:#e6f3ff;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:16px;color:#2666a3;font-weight:bold;pointer-events:none;';
    closeBtn.textContent = '×';
    mainBlock.style.position = 'relative';
    mainBlock.appendChild(closeBtn);
  }
});

let coins = 72;
const coinsSpan = document.querySelector('.vk-coins span:last-child');
document.querySelectorAll('.task-action-vk').forEach(btn => {
  btn.addEventListener('click', function(){
    let amount = 0;
    const text = btn.parentElement.querySelector('.task-reward-vk').textContent;
    const match = text.match(/(\d+)/); if(match) amount = parseInt(match[1]);
    
    // Плавная анимация кристалла
    const popup = document.getElementById('crystal-popup');
    popup.style.display = 'block';
    popup.firstElementChild.style.animation = 'crystal-float 1.2s ease-out';
    setTimeout(() => {popup.style.display='none';}, 1200);
    
    if(/кристалл|монет/.test(text)) {
      coins += amount;
      if (coinsSpan) coinsSpan.textContent = coins + ' кристалла';
    }
  });
});

document.querySelector('.raffle-btn').addEventListener('click', function () {
    // Проверяем достаточно ли кристаллов
    if (coins < 10) {
      alert('Недостаточно кристаллов для участия в розыгрыше!');
      return;
    }
    coins -= 10;
    if (coinsSpan) coinsSpan.textContent = coins + ' кристалла';

    const modal = document.getElementById('fortune-modal');
    const wheel = document.getElementById('wheel-svg');
    wheel.style.transform = 'rotate(0deg)';
    document.getElementById('fortune-result').textContent = 'Вращается...';
    modal.style.display = 'block';
    
    setTimeout(() => {
        const rand = Math.floor(Math.random()*15+5); // 5-19 кристаллов
        const rotations = 720 + Math.floor(Math.random()*360); // случайная финальная позиция
        wheel.style.transform = `rotate(${rotations}deg)`;
        
        setTimeout(() => {
            // Зачисляем выигранные кристаллы на счёт
            coins += rand;
            if (coinsSpan) coinsSpan.textContent = coins + ' кристалла';
            
            document.getElementById('fortune-result').innerHTML =
              `🎉 Поздравляем!<br>Вы выиграли <b style="color:#45bef6;">${rand} кристаллов</b>`;
        }, 3000);
    }, 500);
});
function closeWheel(){document.getElementById('fortune-modal').style.display='none';}
</script>
