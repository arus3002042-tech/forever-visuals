[forever-visuals.html](https://github.com/user-attachments/files/28008802/forever-visuals.html)
<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Forever Visuals — Minecraft Style</title>
<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  :root {
    --main-color: #ff0090;
    --main-color-rgb: 255, 0, 144;
    --second-color: #00ffff;
    --second-color-rgb: 0, 255, 255;
  }

  body {
    background: #0a0a0a;
    width: 100%;
    min-height: 100vh;
    overflow-y: auto;
    overflow-x: hidden;
    font-family: 'Courier New', monospace;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  /* ========== ШАПКА ========== */
  .top-bar {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    height: 60px;
    background: rgba(10, 10, 10, 0.95);
    backdrop-filter: blur(10px);
    z-index: 90;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 0 30px;
    border-bottom: 1px solid rgba(var(--main-color-rgb), 0.3);
  }

  .top-bar-logo {
    color: #fff;
    font-size: 1.3rem;
    letter-spacing: 3px;
    text-shadow: 0 0 15px var(--main-color);
  }

  .account-section {
    display: flex;
    align-items: center;
    gap: 12px;
  }

  .account-btn {
    padding: 10px 20px;
    border-radius: 8px;
    border: 1px solid rgba(var(--main-color-rgb), 0.5);
    background: rgba(var(--main-color-rgb), 0.1);
    color: #fff;
    cursor: pointer;
    font-family: 'Courier New', monospace;
    letter-spacing: 2px;
    font-size: 0.9rem;
    transition: all 0.3s ease;
  }

  .account-btn:hover {
    background: rgba(var(--main-color-rgb), 0.2);
    box-shadow: 0 0 20px rgba(var(--main-color-rgb), 0.3);
  }

  .account-btn.register-btn {
    background: rgba(var(--main-color-rgb), 0.3);
    border-color: var(--main-color);
  }

  .user-info {
    display: none;
    align-items: center;
    gap: 12px;
  }

  .user-avatar {
    width: 38px;
    height: 38px;
    border-radius: 50%;
    background: linear-gradient(135deg, var(--main-color), var(--second-color));
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: bold;
    color: #fff;
    font-size: 1.1rem;
    border: 2px solid #fff;
    box-shadow: 0 0 15px rgba(var(--main-color-rgb), 0.5);
  }

  .user-name {
    color: #fff;
    letter-spacing: 1px;
    text-shadow: 0 0 10px var(--second-color);
  }

  .logout-btn {
    padding: 8px 15px;
    border-radius: 6px;
    border: 1px solid rgba(255, 255, 255, 0.3);
    background: transparent;
    color: #aaa;
    cursor: pointer;
    font-family: 'Courier New', monospace;
    font-size: 0.8rem;
    letter-spacing: 1px;
    transition: all 0.3s ease;
  }

  .logout-btn:hover {
    color: #ff4444;
    border-color: #ff4444;
  }

  /* ========== ПРАВОЕ МЕНЮ ========== */
  .sidebar {
    position: fixed;
    right: 0;
    top: 60px;
    width: 260px;
    height: calc(100% - 60px);
    background: rgba(10, 10, 10, 0.95);
    border-left: 2px solid rgba(var(--main-color-rgb), 0.3);
    backdrop-filter: blur(10px);
    z-index: 100;
    padding: 25px 18px;
    overflow-y: auto;
    box-shadow: -5px 0 30px rgba(var(--main-color-rgb), 0.2);
    display: flex;
    flex-direction: column;
  }

  .menu-logo {
    font-size: 1.4rem;
    font-weight: bold;
    color: #fff;
    text-shadow: 0 0 15px var(--main-color), 0 0 30px var(--second-color);
    text-align: center;
    margin-bottom: 20px;
    letter-spacing: 3px;
  }

  .menu-list {
    list-style: none;
    flex-grow: 1;
  }

  .menu-item {
    margin-bottom: 5px;
  }

  .menu-link {
    display: flex;
    align-items: center;
    gap: 10px;
    padding: 11px 14px;
    color: #aaa;
    text-decoration: none;
    font-size: 0.85rem;
    letter-spacing: 2px;
    border-radius: 8px;
    transition: all 0.3s ease;
    border: 1px solid transparent;
    cursor: pointer;
  }

  .menu-link:hover, .menu-link.active {
    color: #fff;
    background: rgba(var(--main-color-rgb), 0.15);
    border-color: rgba(var(--main-color-rgb), 0.5);
    text-shadow: 0 0 10px var(--main-color);
    box-shadow: 0 0 20px rgba(var(--main-color-rgb), 0.2);
  }

  .menu-icon {
    font-size: 1.1rem;
    width: 22px;
    text-align: center;
  }

  .menu-badge {
    margin-left: auto;
    background: rgba(var(--main-color-rgb), 0.3);
    color: #fff;
    padding: 2px 8px;
    border-radius: 10px;
    font-size: 0.6rem;
    border: 1px solid rgba(var(--main-color-rgb), 0.5);
    animation: badgePulse 2s ease-in-out infinite;
  }

  @keyframes badgePulse {
    0%, 100% { box-shadow: 0 0 5px rgba(var(--main-color-rgb), 0.5); }
    50% { box-shadow: 0 0 15px rgba(var(--main-color-rgb), 0.8); }
  }

  .menu-footer {
    margin-top: auto;
    padding-top: 12px;
    border-top: 1px solid rgba(255, 255, 255, 0.1);
    text-align: center;
    color: #555;
    font-size: 0.7rem;
    letter-spacing: 2px;
  }

  .burger-btn {
    position: fixed;
    top: 75px;
    right: 30px;
    z-index: 99;
    background: rgba(10, 10, 10, 0.8);
    border: 1px solid rgba(var(--main-color-rgb), 0.3);
    color: #fff;
    width: 45px;
    height: 45px;
    border-radius: 10px;
    display: none;
    align-items: center;
    justify-content: center;
    font-size: 1.5rem;
    cursor: pointer;
  }

  /* ========== МОДАЛЬНЫЕ ОКНА ========== */
  .modal-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.85);
    backdrop-filter: blur(5px);
    z-index: 200;
    display: none;
    align-items: center;
    justify-content: center;
  }

  .modal-overlay.active {
    display: flex;
  }

  .modal-window {
    background: rgba(15, 15, 15, 0.98);
    border: 2px solid rgba(var(--main-color-rgb), 0.4);
    border-radius: 16px;
    padding: 35px;
    max-width: 550px;
    width: 90%;
    max-height: 85vh;
    overflow-y: auto;
    position: relative;
    box-shadow: 0 0 50px rgba(var(--main-color-rgb), 0.3);
    animation: modalAppear 0.4s ease;
  }

  @keyframes modalAppear {
    from { transform: scale(0.8); opacity: 0; }
    to { transform: scale(1); opacity: 1; }
  }

  .modal-close {
    position: absolute;
    top: 15px;
    right: 20px;
    background: none;
    border: none;
    color: #aaa;
    font-size: 1.8rem;
    cursor: pointer;
    transition: all 0.3s ease;
    z-index: 10;
  }

  .modal-close:hover {
    color: var(--main-color);
    text-shadow: 0 0 20px var(--main-color);
    transform: rotate(90deg);
  }

  .modal-title {
    font-size: 1.8rem;
    font-weight: bold;
    color: #fff;
    text-shadow: 0 0 20px var(--main-color), 0 0 40px var(--second-color);
    text-align: center;
    letter-spacing: 4px;
    margin-bottom: 20px;
  }

  .form-group {
    margin-bottom: 15px;
  }

  .form-group label {
    display: block;
    color: #aaa;
    letter-spacing: 2px;
    margin-bottom: 6px;
    font-size: 0.85rem;
  }

  .form-group input {
    width: 100%;
    padding: 12px 15px;
    background: rgba(255, 255, 255, 0.05);
    border: 1px solid rgba(255, 255, 255, 0.2);
    border-radius: 8px;
    color: #fff;
    font-family: 'Courier New', monospace;
    font-size: 0.95rem;
    letter-spacing: 1px;
  }

  .form-group input:focus {
    outline: none;
    border-color: var(--main-color);
    box-shadow: 0 0 15px rgba(var(--main-color-rgb), 0.3);
  }

  .submit-btn {
    width: 100%;
    padding: 14px;
    background: linear-gradient(135deg, var(--main-color), var(--second-color));
    border: none;
    border-radius: 10px;
    color: #fff;
    font-family: 'Courier New', monospace;
    font-size: 1.1rem;
    letter-spacing: 3px;
    cursor: pointer;
    margin-top: 10px;
  }

  .error-msg {
    color: #ff4444;
    text-align: center;
    font-size: 0.8rem;
    margin-top: 10px;
    display: none;
  }

  .switch-form {
    text-align: center;
    margin-top: 15px;
    color: #aaa;
    font-size: 0.8rem;
  }

  .switch-form a {
    color: var(--main-color);
    cursor: pointer;
    text-decoration: underline;
  }

  .modal-text {
    color: #ccc;
    font-size: 0.9rem;
    line-height: 1.6;
    text-align: center;
  }

  .modal-highlight {
    color: var(--main-color);
    text-shadow: 0 0 10px var(--main-color);
    font-weight: bold;
  }

  .color-presets {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 12px;
    margin: 20px 0;
  }

  .color-preset {
    width: 100%;
    aspect-ratio: 1;
    border-radius: 12px;
    cursor: pointer;
    border: 3px solid transparent;
    transition: all 0.3s ease;
  }

  .color-preset:hover {
    transform: scale(1.1);
    border-color: #fff;
  }

  .color-preset.active-preset {
    border-color: #fff;
    box-shadow: 0 0 30px currentColor;
  }

  .color-preset.pink { background: linear-gradient(135deg, #ff0090, #ff44aa); }
  .color-preset.blue { background: linear-gradient(135deg, #0090ff, #44aaff); }
  .color-preset.green { background: linear-gradient(135deg, #00ff90, #44ffaa); }
  .color-preset.purple { background: linear-gradient(135deg, #9000ff, #aa44ff); }
  .color-preset.orange { background: linear-gradient(135deg, #ff9000, #ffaa44); }
  .color-preset.cyan { background: linear-gradient(135deg, #00ffff, #44ffff); }
  .color-preset.red { background: linear-gradient(135deg, #ff0000, #ff4444); }
  .color-preset.white { background: linear-gradient(135deg, #ffffff, #cccccc); }

  .color-custom {
    display: flex;
    align-items: center;
    gap: 12px;
    padding: 12px;
    background: rgba(255, 255, 255, 0.05);
    border-radius: 10px;
    flex-wrap: wrap;
  }

  .color-custom label {
    color: #aaa;
    font-size: 0.8rem;
    letter-spacing: 1px;
  }

  .color-custom input[type="color"] {
    width: 40px;
    height: 40px;
    border: 2px solid rgba(255, 255, 255, 0.2);
    border-radius: 8px;
    cursor: pointer;
    background: transparent;
  }

  .reset-btn {
    width: 100%;
    margin-top: 15px;
    padding: 12px;
    background: rgba(255, 255, 255, 0.05);
    border: 1px solid rgba(255, 255, 255, 0.2);
    color: #aaa;
    border-radius: 10px;
    cursor: pointer;
    font-family: 'Courier New', monospace;
    font-size: 0.9rem;
    letter-spacing: 2px;
  }

  /* ========== ОСНОВНОЙ КОНТЕНТ ========== */
  .main-wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    margin-right: 140px;
    margin-top: 60px;
    padding: 40px 20px;
  }

  .visuals-container {
    position: relative;
    width: 700px;
    height: 400px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    flex-shrink: 0;
  }

  .bg-circle {
    position: absolute;
    width: 350px;
    height: 350px;
    border-radius: 50%;
    background: radial-gradient(circle, rgba(var(--main-color-rgb), 0.4) 0%, rgba(var(--second-color-rgb), 0.1) 50%, transparent 70%);
    animation: pulseCircle 3s ease-in-out infinite, rotateHue 6s linear infinite;
    z-index: 0;
  }

  @keyframes pulseCircle {
    0%, 100% { transform: scale(1); opacity: 0.7; }
    50% { transform: scale(1.3); opacity: 1; }
  }

  @keyframes rotateHue {
    0% { filter: hue-rotate(0deg); }
    100% { filter: hue-rotate(360deg); }
  }

  .main-title {
    font-size: 4rem;
    font-weight: bold;
    text-transform: uppercase;
    letter-spacing: 10px;
    color: #fff;
    text-shadow: 0 0 20px var(--main-color), 0 0 40px var(--second-color);
    animation: textPulse 2s ease-in-out infinite, glitch 3s infinite;
    z-index: 2;
  }

  @keyframes textPulse {
    0%, 100% { transform: scale(1); }
    50% { transform: scale(1.05); text-shadow: 0 0 30px var(--main-color), 0 0 60px var(--second-color); }
  }

  @keyframes glitch {
    0%, 90%, 100% { transform: translate(0); }
    92% { transform: translate(-3px, 2px); }
    94% { transform: translate(3px, -2px); }
    96% { transform: translate(-2px, -1px); }
    98% { transform: translate(2px, 1px); }
  }

  .subtitle {
    font-size: 1.3rem;
    color: #aaa;
    letter-spacing: 5px;
    margin-top: 15px;
    text-shadow: 0 0 10px var(--second-color);
    z-index: 2;
    animation: subtitleFade 2s ease-in-out infinite alternate;
  }

  @keyframes subtitleFade {
    from { opacity: 0.4; }
    to { opacity: 1; }
  }

  .particle {
    position: absolute;
    width: 6px;
    height: 6px;
    background: var(--main-color);
    border-radius: 50%;
    box-shadow: 0 0 10px var(--main-color), 0 0 20px var(--second-color);
    z-index: 1;
    animation: floatUp 5s linear infinite;
    opacity: 0;
  }

  @keyframes floatUp {
    0% { transform: translateY(100vh) scale(0); opacity: 0; }
    20% { opacity: 1; }
    80% { opacity: 1; }
    100% { transform: translateY(-10vh) scale(1.5); opacity: 0; }
  }

  .line {
    position: absolute;
    height: 2px;
    width: 55%;
    background: linear-gradient(90deg, transparent, var(--main-color), var(--second-color), transparent);
    z-index: 1;
    animation: lineMove 4s linear infinite;
  }

  .line.top { top: 30%; }
  .line.bottom { top: 70%; animation-delay: 2s; }

  @keyframes lineMove {
    0% { transform: translateX(-100%); opacity: 0; }
    10% { opacity: 1; }
    90% { opacity: 1; }
    100% { transform: translateX(100%); opacity: 0; }
  }

  /* ========== БЛОК "СКАЧАТЬ МОД" ========== */
  .download-section {
    width: 100%;
    max-width: 700px;
    margin-top: 50px;
    padding: 40px;
    background: rgba(15, 15, 15, 0.95);
    border: 2px solid rgba(var(--main-color-rgb), 0.4);
    border-radius: 20px;
    text-align: center;
    box-shadow: 0 0 50px rgba(var(--main-color-rgb), 0.2);
  }

  .download-title {
    font-size: 1.8rem;
    font-weight: bold;
    color: #fff;
    letter-spacing: 4px;
    text-shadow: 0 0 20px var(--main-color), 0 0 40px var(--second-color);
    margin-bottom: 10px;
  }

  .download-subtitle {
    color: #888;
    font-size: 0.85rem;
    letter-spacing: 2px;
    margin-bottom: 30px;
  }

  .download-info {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 20px;
    margin-bottom: 30px;
  }

  .info-card {
    background: rgba(255, 255, 255, 0.03);
    border: 1px solid rgba(var(--main-color-rgb), 0.2);
    border-radius: 12px;
    padding: 20px;
    text-align: center;
  }

  .info-card-icon {
    font-size: 2rem;
    margin-bottom: 10px;
  }

  .info-card-title {
    color: var(--second-color);
    font-size: 0.8rem;
    letter-spacing: 2px;
    margin-bottom: 5px;
  }

  .info-card-value {
    color: #fff;
    font-size: 1.2rem;
    font-weight: bold;
    letter-spacing: 1px;
  }

  .download-btn {
    display: inline-block;
    padding: 18px 50px;
    background: linear-gradient(135deg, var(--main-color), var(--second-color));
    border: none;
    border-radius: 15px;
    color: #fff;
    font-family: 'Courier New', monospace;
    font-size: 1.3rem;
    letter-spacing: 4px;
    cursor: pointer;
    text-decoration: none;
    transition: all 0.3s ease;
    position: relative;
    overflow: hidden;
  }

  .download-btn:hover {
    transform: translateY(-3px);
    box-shadow: 0 0 40px rgba(var(--main-color-rgb), 0.6);
  }

  .download-btn::after {
    content: '';
    position: absolute;
    top: -50%;
    left: -50%;
    width: 200%;
    height: 200%;
    background: linear-gradient(45deg, transparent, rgba(255,255,255,0.1), transparent);
    animation: btnShine 3s infinite;
  }

  @keyframes btnShine {
    0% { transform: translateX(-100%) rotate(45deg); }
    100% { transform: translateX(100%) rotate(45deg); }
  }

  .version-tags {
    display: flex;
    justify-content: center;
    gap: 10px;
    margin-top: 20px;
    flex-wrap: wrap;
  }

  .version-tag {
    padding: 5px 15px;
    background: rgba(255, 255, 255, 0.05);
    border: 1px solid rgba(255, 255, 255, 0.2);
    border-radius: 20px;
    color: #aaa;
    font-size: 0.75rem;
    letter-spacing: 1px;
  }

  /* ========== ХАРАКТЕРИСТИКИ ПК ========== */
  .specs-section {
    width: 100%;
    max-width: 700px;
    margin-top: 40px;
    padding: 30px;
    background: rgba(15, 15, 15, 0.9);
    border: 2px solid rgba(var(--main-color-rgb), 0.3);
    border-radius: 16px;
  }

  .specs-section-title {
    text-align: center;
    color: #fff;
    font-size: 1.3rem;
    letter-spacing: 4px;
    text-shadow: 0 0 15px var(--main-color);
    margin-bottom: 25px;
  }

  .specs-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 25px;
  }

  .specs-column h4 {
    color: var(--main-color);
    text-shadow: 0 0 10px var(--main-color);
    letter-spacing: 2px;
    margin-bottom: 10px;
    font-size: 0.85rem;
    border-bottom: 1px solid rgba(var(--main-color-rgb), 0.3);
    padding-bottom: 6px;
  }

  .spec-row {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 5px 0;
    color: #ccc;
    font-size: 0.72rem;
    letter-spacing: 1px;
  }

  .spec-name {
    color: #aaa;
  }

  .power-indicator {
    display: flex;
    gap: 4px;
  }

  .power-dot {
    width: 7px;
    height: 7px;
    border-radius: 50%;
    background: #333;
  }

  .power-dot.low { background: #44ff44; box-shadow: 0 0 5px #44ff44; }
  .power-dot.mid { background: #ffff00; box-shadow: 0 0 5px #ffff00; }
  .power-dot.ultra { background: #ff0044; box-shadow: 0 0 7px #ff0044; }

  .spec-note {
    color: #888;
    font-size: 0.7rem;
    text-align: center;
    margin-top: 20px;
    font-style: italic;
  }

  /* ========== АДАПТИВНОСТЬ ========== */
  @media (max-width: 768px) {
    .sidebar {
      transform: translateX(100%);
    }
    .sidebar.open {
      transform: translateX(0);
    }
    .burger-btn {
      display: flex;
    }
    .main-wrapper {
      margin-right: 0;
      padding: 20px 10px;
    }
    .visuals-container {
      width: 100%;
      height: 300px;
    }
    .main-title {
      font-size: 2rem;
    }
    .specs-grid, .download-info {
      grid-template-columns: 1fr;
    }
    .top-bar {
      padding: 0 15px;
    }
  }
</style>
</head>
<body>

<div class="top-bar">
  <div class="top-bar-logo">FOREVER VISUALS</div>
  <div class="account-section">
    <button class="account-btn" onclick="showModal('authModal')">ВОЙТИ</button>
    <button class="account-btn register-btn" onclick="showModal('authModal'); switchAuthForm('register')">РЕГИСТРАЦИЯ</button>
    <div class="user-info" id="userInfo">
      <div class="user-avatar" id="userAvatar"></div>
      <span class="user-name" id="userNameDisplay"></span>
      <button class="logout-btn" onclick="logout()">ВЫХОД</button>
    </div>
  </div>
</div>

<button class="burger-btn" onclick="document.getElementById('sidebar').classList.toggle('open')">☰</button>

<aside class="sidebar" id="sidebar">
  <div class="menu-logo">МЕНЮ</div>
  <ul class="menu-list">
    <li class="menu-item"><a class="menu-link active"><span class="menu-icon">🏠</span> Главная</a></li>
    <li class="menu-item"><a class="menu-link"><span class="menu-icon">⚡</span> Эффекты <span class="menu-badge">NEW</span></a></li>
    <li class="menu-item"><a class="menu-link"><span class="menu-icon">🎨</span> Шейдеры</a></li>
    <li class="menu-item"><a class="menu-link"><span class="menu-icon">📦</span> Ресурспаки</a></li>
    <li class="menu-item"><a class="menu-link" onclick="showModal('settingsModal')"><span class="menu-icon">⚙️</span> Настройки</a></li>
    <li class="menu-item"><a class="menu-link" onclick="showModal('aboutModal')"><span class="menu-icon">ℹ️</span> О проекте</a></li>
  </ul>
  <div class="menu-footer">FOREVER VISUALS v1.0</div>
</aside>

<div class="main-wrapper">
  
  <div class="visuals-container">
    <div class="bg-circle"></div>
    <div class="line top"></div>
    <h1 class="main-title">FOREVER</h1>
    <p class="subtitle">VISUALS // MINECRAFT</p>
    <div class="line bottom"></div>
  </div>

  <!-- БЛОК СКАЧИВАНИЯ МОДА -->
  <div class="download-section">
    <div class="download-title">СКАЧАТЬ МОД</div>
    <div class="download-subtitle">Forever Visuals для Minecraft</div>
    
    <div class="download-info">
      <div class="info-card">
        <div class="info-card-icon">📦</div>
        <div class="info-card-title">ВЕРСИЯ МОДА</div>
        <div class="info-card-value">1.0.0</div>
      </div>
      <div class="info-card">
        <div class="info-card-icon">🎮</div>
        <div class="info-card-title">ИГРА</div>
        <div class="info-card-value">1.20.4</div>
      </div>
      <div class="info-card">
        <div class="info-card-icon">⚙️</div>
        <div class="info-card-title">ЗАГРУЗЧИК</div>
        <div class="info-card-value">Fabric</div>
      </div>
    </div>

    <button class="download-btn" onclick="downloadMod()">СКАЧАТЬ</button>
    
    <div class="version-tags">
      <span class="version-tag">Minecraft 1.20.4</span>
      <span class="version-tag">Fabric API</span>
      <span class="version-tag">Shader Support</span>
    </div>
  </div>

  <!-- ХАРАКТЕРИСТИКИ ПК -->
  <div class="specs-section">
    <div class="specs-section-title">💻 ХАРАКТЕРИСТИКИ ПК</div>
    <div class="specs-grid">
      <div class="specs-column">
        <h4>🔲 ПРОЦЕССОРЫ INTEL</h4>
        <div class="spec-row"><span class="spec-name">Core i3</span><span class="power-indicator"><span class="power-dot low"></span><span class="power-dot low"></span><span class="power-dot"></span><span class="power-dot"></span></span></div>
        <div class="spec-row"><span class="spec-name">Core i5</span><span class="power-indicator"><span class="power-dot low"></span><span class="power-dot low"></span><span class="power-dot low"></span><span class="power-dot"></span></span></div>
        <div class="spec-row"><span class="spec-name">Core i7</span><span class="power-indicator"><span class="power-dot low"></span><span class="power-dot low"></span><span class="power-dot low"></span><span class="power-dot mid"></span></span></div>
        <div class="spec-row"><span class="spec-name">Core i9</span><span class="power-indicator"><span class="power-dot low"></span><span class="power-dot low"></span><span class="power-dot low"></span><span class="power-dot ultra"></span></span></div>
        <h4 style="margin-top: 18px;">🔲 AMD</h4>
        <div class="spec-row"><span class="spec-name">Ryzen 3</span><span class="power-indicator"><span class="power-dot low"></span><span class="power-dot low"></span><span class="power-dot"></span><span class="power-dot"></span></span></div>
        <div class="spec-row"><span class="spec-name">Ryzen 5</span><span class="power-indicator"><span class="power-dot low"></span><span class="power-dot low"></span><span class="power-dot low"></span><span class="power-dot"></span></span></div>
        <div class="spec-row"><span class="spec-name">Ryzen 7</span><span class="power-indicator"><span class="power-dot low"></span><span class="power-dot low"></span><span class="power-dot low"></span><span class="power-dot mid"></span></span></div>
        <div class="spec-row"><span class="spec-name">Ryzen 9</span><span class="power-indicator"><span class="power-dot low"></span><span class="power-dot low"></span><span class="power-dot low"></span><span class="power-dot ultra"></span></span></div>
      </div>
      <div class="specs-column">
        <h4>🎮 ВИДЕОКАРТЫ NVIDIA</h4>
        <div class="spec-row"><span class="spec-name">GTX 550 – 1050</span><span class="power-indicator"><span class="power-dot low"></span><span class="power-dot"></span><span class="power-dot"></span><span class="power-dot"></span></span></div>
        <div class="spec-row"><span class="spec-name">GTX 1060 – 1660</span><span class="power-indicator"><span class="power-dot low"></span><span class="power-dot low"></span><span class="power-dot"></span><span class="power-dot"></span></span></div>
        <div class="spec-row"><span class="spec-name">RTX 2060 – 3060</span><span class="power-indicator"><span class="power-dot low"></span><span class="power-dot low"></span><span class="power-dot low"></span><span class="power-dot"></span></span></div>
        <div class="spec-row"><span class="spec-name">RTX 3070 – 4070</span><span class="power-indicator"><span class="power-dot low"></span><span class="power-dot low"></span><span class="power-dot low"></span><span class="power-dot mid"></span></span></div>
        <div class="spec-row"><span class="spec-name">RTX 4080 – 5090</span><span class="power-indicator"><span class="power-dot low"></span><span class="power-dot low"></span><span class="power-dot low"></span><span class="power-dot ultra"></span></span></div>
        <h4 style="margin-top: 18px;">🎮 AMD</h4>
        <div class="spec-row"><span class="spec-name">RX 550 – 580</span><span class="power-indicator"><span class="power-dot low"></span><span class="power-dot"></span><span class="power-dot"></span><span class="power-dot"></span></span></div>
        <div class="spec-row"><span class="spec-name">RX 590 – 5700</span><span class="power-indicator"><span class="power-dot low"></span><span class="power-dot low"></span><span class="power-dot"></span><span class="power-dot"></span></span></div>
        <div class="spec-row"><span class="spec-name">RX 6600 – 6800</span><span class="power-indicator"><span class="power-dot low"></span><span class="power-dot low"></span><span class="power-dot low"></span><span class="power-dot"></span></span></div>
        <div class="spec-row"><span class="spec-name">RX 6900 – 7900 XTX</span><span class="power-indicator"><span class="power-dot low"></span><span class="power-dot low"></span><span class="power-dot low"></span><span class="power-dot ultra"></span></span></div>
      </div>
    </div>
    <div class="spec-note">💡 Рекомендуем: Intel Core i5 / AMD Ryzen 5 + GTX 1660 / RTX 3060</div>
  </div>

</div>

<!-- ОКНО АВТОРИЗАЦИИ -->
<div class="modal-overlay" id="authModal">
  <div class="modal-window">
    <button class="modal-close" onclick="closeModal('authModal')">✕</button>
    <div class="modal-title" id="authTitle">ВХОД</div>
    <div id="loginForm">
      <div class="form-group"><label>ЛОГИН</label><input type="text" id="loginUsername" placeholder="Введите логин..."></div>
      <div class="form-group"><label>ПАРОЛЬ</label><input type="password" id="loginPassword" placeholder="Введите пароль..."></div>
      <div class="error-msg" id="loginError"></div>
      <button class="submit-btn" onclick="login()">ВОЙТИ</button>
      <div class="switch-form">Нет аккаунта? <a onclick="switchAuthForm('register')">Регистрация</a></div>
    </div>
    <div id="registerForm" style="display: none;">
      <div class="form-group"><label>ЛОГИН</label><input type="text" id="regUsername" placeholder="Придумайте логин..."></div>
      <div class="form-group"><label>EMAIL</label><input type="email" id="regEmail" placeholder="Введите email..."></div>
      <div class="form-group"><label>ПАРОЛЬ</label><input type="password" id="regPassword" placeholder="Придумайте пароль..."></div>
      <div class="form-group"><label>ПОВТОРИТЕ ПАРОЛЬ</label><input type="password" id="regPasswordConfirm" placeholder="Повторите пароль..."></div>
      <div class="error-msg" id="regError"></div>
      <button class="submit-btn" onclick="register()">РЕГИСТРАЦИЯ</button>
      <div class="switch-form">Уже есть аккаунт? <a onclick="switchAuthForm('login')">Войти</a></div>
    </div>
  </div>
</div>

<!-- ОКНО НАСТРОЕК -->
<div class="modal-overlay" id="settingsModal">
  <div class="modal-window">
    <button class="modal-close" onclick="closeModal('settingsModal')">✕</button>
    <div class="modal-title">НАСТРОЙКИ</div>
    <div class="modal-text" style="margin-bottom:15px;">Выберите цветовую тему</div>
    <div class="color-presets">
      <div class="color-preset pink active-preset" data-color="#ff0090" data-second="#00ffff" onclick="setPresetColor(this)"></div>
      <div class="color-preset blue" data-color="#0090ff" data-second="#ff00ff" onclick="setPresetColor(this)"></div>
      <div class="color-preset green" data-color="#00ff90" data-second="#ffff00" onclick="setPresetColor(this)"></div>
      <div class="color-preset purple" data-color="#9000ff" data-second="#00ffaa" onclick="setPresetColor(this)"></div>
      <div class="color-preset orange" data-color="#ff9000" data-second="#00aaff" onclick="setPresetColor(this)"></div>
      <div class="color-preset cyan" data-color="#00ffff" data-second="#ff0090" onclick="setPresetColor(this)"></div>
      <div class="color-preset red" data-color="#ff0000" data-second="#ff8800" onclick="setPresetColor(this)"></div>
      <div class="color-preset white" data-color="#ffffff" data-second="#aaaaaa" onclick="setPresetColor(this)"></div>
    </div>
    <div class="color-custom">
      <label>Осн:</label><input type="color" id="mainColorPicker" value="#ff0090" onchange="setCustomColor()">
      <label>Вт:</label><input type="color" id="secondColorPicker" value="#00ffff" onchange="setCustomColor()">
    </div>
    <button class="reset-btn" onclick="resetColors()">СБРОСИТЬ</button>
  </div>
</div>

<!-- ОКНО О ПРОЕКТЕ -->
<div class="modal-overlay" id="aboutModal">
  <div class="modal-window">
    <button class="modal-close" onclick="closeModal('aboutModal')">✕</button>
    <div class="modal-title">О ПРОЕКТЕ</div>
    <div class="modal-text">
      <p><span class="modal-highlight">Forever Visuals</span> — мод для Minecraft, добавляющий анимированные HUD, неоновые шейдеры, пульсирующие текстуры и искажения экрана.</p>
      <p style="margin-top:15px;">Полная кастомизация через настройки. Поддержка шейдеров.</p>
    </div>
  </div>
</div>

<script>
// ========== ЦВЕТА ==========
function applyColors(main, second) {
  const root = document.documentElement;
  root.style.setProperty('--main-color', main);
  root.style.setProperty('--main-color-rgb', `${parseInt(main.slice(1,3),16)}, ${parseInt(main.slice(3,5),16)}, ${parseInt(main.slice(5,7),16)}`);
  root.style.setProperty('--second-color', second);
  root.style.setProperty('--second-color-rgb', `${parseInt(second.slice(1,3),16)}, ${parseInt(second.slice(3,5),16)}, ${parseInt(second.slice(5,7),16)}`);
  document.getElementById('mainColorPicker').value = main;
  document.getElementById('secondColorPicker').value = second;
  localStorage.setItem('fvMainColor', main);
  localStorage.setItem('fvSecondColor', second);
}

function setPresetColor(el) {
  document.querySelectorAll('.color-preset').forEach(p => p.classList.remove('active-preset'));
  el.classList.add('active-preset');
  applyColors(el.dataset.color, el.dataset.second);
}

function setCustomColor() {
  document.querySelectorAll('.color-preset').forEach(p => p.classList.remove('active-preset'));
  applyColors(document.getElementById('mainColorPicker').value, document.getElementById('secondColorPicker').value);
}

function resetColors() {
  applyColors('#ff0090', '#00ffff');
  document.querySelectorAll('.color-preset').forEach(p => p.classList.remove('active-preset'));
  document.querySelector('.color-preset.pink').classList.add('active-preset');
}

(function() {
  applyColors(localStorage.getItem('fvMainColor') || '#ff0090', localStorage.getItem('fvSecondColor') || '#00ffff');
})();

// ========== МОДАЛКИ ==========
function showModal(id) { document.getElementById(id).classList.add('active'); }
function closeModal(id) { document.getElementById(id).classList.remove('active'); }
document.querySelectorAll('.modal-overlay').forEach(o => o.addEventListener('click', function(e) { if (e.target === this) this.classList.remove('active'); }));
document.addEventListener('keydown', function(e) { if (e.key === 'Escape') document.querySelectorAll('.modal-overlay.active').forEach(o => o.classList.remove('active')); });

// ========== АВТОРИЗАЦИЯ ==========
function switchAuthForm(f) {
  document.getElementById('loginForm').style.display = f === 'login' ? 'block' : 'none';
  document.getElementById('registerForm').style.display = f === 'register' ? 'block' : 'none';
  document.getElementById('authTitle').textContent = f === 'login' ? 'ВХОД' : 'РЕГИСТРАЦИЯ';
  document.querySelectorAll('.error-msg').forEach(e => { e.style.display = 'none'; e.textContent = ''; });
}

function login() {
  const u = document.getElementById('loginUsername').value.trim();
  const p = document.getElementById('loginPassword').value.trim();
  const err = document.getElementById('loginError');
  if (!u || !p) { err.textContent = 'Заполните все поля'; err.style.display = 'block'; return; }
  const users = JSON.parse(localStorage.getItem('fvUsers') || '{}');
  if (!users[u] || users[u] !== p) { err.textContent = 'Неверный логин или пароль'; err.style.display = 'block'; return; }
  setLoggedIn(u);
  closeModal('authModal');
}

function register() {
  const u = document.getElementById('regUsername').value.trim();
  const e = document.getElementById('regEmail').value.trim();
  const p = document.getElementById('regPassword').value.trim();
  const pc = document.getElementById('regPasswordConfirm').value.trim();
  const err = document.getElementById('regError');
  if (!u || !e || !p) { err.textContent = 'Заполните все поля'; err.style.display = 'block'; return; }
  if (p !== pc) { err.textContent = 'Пароли не совпадают'; err.style.display = 'block'; return; }
  if (p.length < 4) { err.textContent = 'Минимум 4 символа'; err.style.display = 'block'; return; }
  const users = JSON.parse(localStorage.getItem('fvUsers') || '{}');
  if (users[u]) { err.textContent = 'Пользователь существует'; err.style.display = 'block'; return; }
  users[u] = p;
  localStorage.setItem('fvUsers', JSON.stringify(users));
  setLoggedIn(u);
  closeModal('authModal');
}

function setLoggedIn(username) {
  localStorage.setItem('fvCurrentUser', username);
  document.getElementById('userAvatar').textContent = username[0].toUpperCase();
  document.getElementById('userNameDisplay').textContent = username;
  document.querySelectorAll('.account-btn').forEach(b => b.style.display = 'none');
  document.getElementById('userInfo').style.display = 'flex';
}

function logout() {
  localStorage.removeItem('fvCurrentUser');
  document.querySelectorAll('.account-btn').forEach(b => b.style.display = 'inline-block');
  document.getElementById('userInfo').style.display = 'none';
}

(function() {
  const u = localStorage.getItem('fvCurrentUser');
  if (u) setLoggedIn(u);
})();

// ========== СКАЧИВАНИЕ МОДА ==========
function downloadMod() {
  alert('Мод Forever Visuals v1.0.0 для Minecraft 1.20.4 (Fabric)\n\nСкачивание начнётся после регистрации на сайте.');
}

// ========== ЧАСТИЦЫ ==========
setInterval(function() {
  const p = document.createElement('div');
  p.classList.add('particle');
  p.style.left = Math.random() * 100 + '%';
  p.style.animationDelay = Math.random() * 5 + 's';
  p.style.width = p.style.height = (Math.random() * 6 + 4) + 'px';
  document.body.appendChild(p);
  setTimeout(function() { p.remove(); }, 6000);
}, 200);

// ========== МЫШЬ ==========
document.addEventListener('mousemove', function(e) {
  const c = document.querySelector('.bg-circle');
  if (c) c.style.transform = `translate(${(e.clientX/window.innerWidth-0.5)*20}px, ${(e.clientY/window.innerHeight-0.5)*20}px)`;
});
</script>

</body>
</html>
