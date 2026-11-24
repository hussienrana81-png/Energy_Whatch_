<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Energy Watch</title>

<style>
:root {
    --green: #183d2d;
    --green2: #315d42;
    --light-green: #74a943;
    --cream: #f7f7f2;
    --card: #fbfaf6;
    --border: #e2e4dc;
    --muted: #788176;
    --soft: #e9eee0;
}

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: Arial, sans-serif;
}

body {
    background: var(--cream);
    color: var(--green);
    min-height: 100vh;
}

button, input, select {
    font: inherit;
}

button { cursor: pointer; }
.hidden { display: none !important; }

/* AUTH */
.auth-wrapper {
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 25px;
}

.auth-container {
    width: 100%;
    max-width: 1050px;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 45px;
    align-items: center;
}

.phone {
    min-height: 820px;
    background: var(--card);
    border: 2px solid #deded8;
    border-radius: 42px;
    overflow: hidden;
    position: relative;
    box-shadow: 0 10px 25px #00000012;
    padding: 30px 40px;
    display: flex;
    flex-direction: column;
    align-items: center;
}

.phone::before {
    content: "";
    position: absolute;
    width: 350px;
    height: 250px;
    background: var(--soft);
    border-radius: 0 0 100% 100%;
    top: -150px;
    right: -50px;
}

.phone > * { position: relative; z-index: 1; }

.logo {
    text-align: center;
    margin-top: 90px;
}

.logo-icon { font-size: 85px; color: var(--green); }

.logo h1 {
    font-size: 43px;
    letter-spacing: -2px;
    margin-top: 10px;
}

.logo h1 span { color: var(--light-green); }

.tagline { margin-top: 12px; font-size: 18px; }

.city {
    height: 120px;
    width: calc(100% + 80px);
    margin-top: 25px;
    background: linear-gradient(to top, #a8c69c, #edf2e7);
    clip-path: polygon(0 65%,12% 50%,22% 65%,35% 38%,50% 60%,63% 35%,77% 60%,90% 30%,100% 55%,100% 100%,0 100%);
}

.auth-form { width: 100%; margin-top: 20px; }

.input-box {
    width: 100%;
    min-height: 58px;
    border: 1px solid #d9d9d2;
    border-radius: 20px;
    display: flex;
    align-items: center;
    padding: 0 17px;
    margin-bottom: 14px;
    background: #f8f7f2;
    transition: .3s;
}

.input-box:focus-within {
    border-color: var(--green2);
    box-shadow: 0 0 0 3px #315d4215;
}

.input-box .icon { font-size: 21px; margin-right: 15px; }

.input-box input {
    width: 100%;
    border: none;
    outline: none;
    background: transparent;
    font-size: 16px;
    color: var(--green);
}

.eye { cursor: pointer; color: #777; }

.main-btn {
    width: 100%;
    min-height: 58px;
    border: none;
    border-radius: 35px;
    background: linear-gradient(110deg, #173c29, #315d42);
    color: white;
    font-size: 18px;
    font-weight: bold;
    transition: .3s;
}

.main-btn:hover {
    transform: translateY(-2px);
    box-shadow: 0 7px 15px #173c2930;
}

.main-btn:disabled, .google-btn:disabled {
    opacity: .6;
    cursor: wait;
}

.options {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin: 17px 0 22px;
    font-size: 14px;
    color: #222;
}

.remember { display: flex; align-items: center; gap: 7px; }
.remember input { accent-color: var(--green); }

a {
    color: var(--green);
    font-weight: bold;
    cursor: pointer;
    text-decoration: none;
}

.divider {
    display: flex;
    align-items: center;
    gap: 12px;
    margin: 17px 0;
    color: #777;
    width: 100%;
}

.divider::before, .divider::after {
    content: "";
    flex: 1;
    height: 1px;
    background: #d3d3cc;
}

.google-btn {
    width: 100%;
    min-height: 52px;
    border: 1px solid var(--green);
    border-radius: 30px;
    background: transparent;
    font-size: 16px;
}

.google-icon { color: #4285f4; font-weight: bold; margin-right: 10px; }

.bottom-text {
    margin-top: 25px;
    text-align: center;
    color: #222;
}

.bottom-text a { margin-left: 5px; }
.signup { display: none; }

.signup .top {
    width: 100%;
    margin-top: 55px;
    text-align: center;
}

.back {
    width: 48px;
    height: 48px;
    border-radius: 50%;
    border: 1px solid #ddd;
    background: white;
    font-size: 23px;
    display: block;
    margin-bottom: 30px;
}

.signup h2 { font-size: 32px; margin-bottom: 12px; }

.signup .subtitle {
    font-size: 16px;
    line-height: 1.5;
    color: #555;
}

.signup .auth-form { margin-top: 25px; }

.decoration {
    position: absolute;
    bottom: 0;
    left: 0;
    width: 100%;
    height: 80px;
    background: linear-gradient(170deg, transparent 20%, #e4eedb 21%, #8eae78 75%, #315a39);
    clip-path: polygon(0 40%,20% 60%,45% 80%,70% 50%,100% 35%,100% 100%,0 100%);
}

/* DASHBOARD */
#dashboard { display: none; min-height: 100vh; }

.sidebar {
    width: 255px;
    background: #183d2d;
    color: white;
    position: fixed;
    top: 0;
    bottom: 0;
    left: 0;
    padding: 30px 18px;
    z-index: 10;
    display: flex;
    flex-direction: column;
}

.side-logo {
    font-size: 25px;
    font-weight: bold;
    padding: 8px 12px 35px;
}

.side-logo span { color: #a4cf70; }

.nav-title {
    color: #b6c8b8;
    font-size: 11px;
    letter-spacing: 2px;
    margin: 10px 12px 14px;
}

.nav-link {
    display: flex;
    align-items: center;
    gap: 13px;
    padding: 14px 15px;
    margin-bottom: 7px;
    color: #e7eee6;
    border-radius: 13px;
    cursor: pointer;
    transition: .25s;
    font-size: 15px;
}

.nav-link:hover, .nav-link.active {
    background: #315d42;
    color: white;
}

.nav-link .nav-icon { font-size: 19px; width: 23px; }
.sidebar-bottom { margin-top: auto; }

.user-mini {
    border-top: 1px solid #ffffff25;
    padding: 20px 8px 10px;
    display: flex;
    align-items: center;
    gap: 10px;
    overflow: hidden;
}

.avatar {
    width: 38px;
    height: 38px;
    border-radius: 50%;
    background: #a4c77c;
    color: var(--green);
    display: grid;
    place-items: center;
    font-weight: bold;
    flex-shrink: 0;
}

.user-mini small {
    color: #c5d4c8;
    display: block;
    margin-top: 4px;
    overflow-wrap: anywhere;
}

.main-area {
    margin-left: 255px;
    padding: 35px 40px;
    max-width: 1600px;
}

.topbar {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 15px;
    margin-bottom: 30px;
}

.topbar h1 { font-size: 30px; }
.topbar p { color: var(--muted); margin-top: 7px; }
.top-actions { display: flex; gap: 10px; align-items: center; }

.date-label {
    background: white;
    border: 1px solid var(--border);
    padding: 11px 15px;
    border-radius: 12px;
    color: #596354;
    font-size: 13px;
}

.content-section { display: none; animation: fadeIn .3s ease; }
.content-section.active { display: block; }

@keyframes fadeIn {
    from { opacity: 0; transform: translateY(8px); }
    to { opacity: 1; transform: translateY(0); }
}

.welcome-banner {
    background: linear-gradient(115deg, #183d2d, #426c47);
    color: white;
    border-radius: 22px;
    padding: 28px 30px;
    margin-bottom: 25px;
    position: relative;
    overflow: hidden;
}

.welcome-banner::after {
    content: "🌿";
    position: absolute;
    right: 35px;
    top: 15px;
    font-size: 90px;
    opacity: .18;
}

.welcome-banner h2 { font-size: 25px; margin-bottom: 10px; }
.welcome-banner p { color: #e1eadf; line-height: 1.6; max-width: 550px; }

.stats-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 17px;
    margin-bottom: 25px;
}

.stat-card, .panel, .device-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 18px;
    padding: 22px;
    box-shadow: 0 5px 15px #00000005;
}

.stat-card { transition: .25s; }

.stat-card:hover, .device-card:hover {
    transform: translateY(-4px);
    box-shadow: 0 9px 22px #183d2d12;
}

.stat-icon {
    width: 43px;
    height: 43px;
    border-radius: 13px;
    background: var(--soft);
    display: grid;
    place-items: center;
    font-size: 22px;
    margin-bottom: 15px;
}

.stat-card p { color: var(--muted); font-size: 13px; }
.stat-card h2 { font-size: 25px; margin: 8px 0; }
.stat-card small { color: var(--muted); }

.two-columns {
    display: grid;
    grid-template-columns: 1.3fr 1fr;
    gap: 18px;
    margin-bottom: 22px;
}

.panel h3 { font-size: 18px; margin-bottom: 8px; }
.panel-subtitle { color: var(--muted); font-size: 13px; margin-bottom: 20px; }

.section-heading {
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 15px;
    margin: 28px 0 16px;
}

.section-heading h2 { font-size: 21px; }

.small-btn {
    border: none;
    background: var(--green);
    color: white;
    padding: 11px 17px;
    border-radius: 12px;
    font-weight: bold;
}

.small-btn:hover { background: var(--green2); }

.outline-btn {
    background: transparent;
    border: 1px solid var(--green);
    color: var(--green);
    padding: 10px 15px;
    border-radius: 12px;
    font-weight: bold;
}

.device-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 16px;
}

.device-card { transition: .25s; }

.device-top {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 18px;
}

.device-emoji {
    width: 48px;
    height: 48px;
    border-radius: 14px;
    background: var(--soft);
    display: grid;
    place-items: center;
    font-size: 25px;
}

.status {
    font-size: 11px;
    border-radius: 20px;
    padding: 6px 10px;
    background: #e9eee0;
    color: #426c47;
}

.status.off { background: #eeeeeb; color: #777; }

.device-card h3 { margin-bottom: 7px; font-size: 17px; }
.device-card p { color: var(--muted); font-size: 13px; margin-bottom: 15px; }

.device-metrics {
    display: flex;
    justify-content: space-between;
    border-top: 1px solid var(--border);
    padding-top: 13px;
    font-size: 13px;
}

.device-actions { display: flex; gap: 8px; margin-top: 15px; }

.device-actions button {
    flex: 1;
    padding: 9px 5px;
    border-radius: 10px;
    border: 1px solid var(--border);
    background: white;
    color: var(--green);
    font-size: 12px;
    font-weight: bold;
}

.device-actions button:hover { background: var(--soft); }

.device-actions .delete-btn {
    color: #a52d2d;
    border-color: #e8caca;
}

.progress-track {
    width: 100%;
    height: 10px;
    background: #e9ece5;
    border-radius: 20px;
    overflow: hidden;
    margin: 12px 0;
}

.progress-fill {
    height: 100%;
    background: linear-gradient(90deg, #315d42, #8dbd5d);
    border-radius: 20px;
}

.budget-line {
    display: flex;
    justify-content: space-between;
    gap: 10px;
    font-size: 13px;
    color: var(--muted);
}

.energy-list { display: flex; flex-direction: column; gap: 17px; }

.energy-item {
    display: grid;
    grid-template-columns: 35px 1fr auto;
    gap: 10px;
    align-items: center;
}

.energy-item .energy-emoji { font-size: 21px; }
.energy-item small { display: block; color: var(--muted); margin-top: 5px; font-size: 12px; }
.energy-item strong { font-size: 13px; }
.energy-item .progress-track { margin: 7px 0 0; height: 7px; }

/* ENERGY MAP */
.map-layout {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 20px;
}

.donut-area {
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 290px;
}

.donut {
    width: 220px;
    height: 220px;
    border-radius: 50%;
    background: conic-gradient(#315d42 0deg 120deg, #8dbd5d 120deg 220deg, #b7c9a7 220deg 290deg, #dce6d1 290deg 360deg);
    display: grid;
    place-items: center;
    position: relative;
}

.donut::before {
    content: "";
    position: absolute;
    width: 145px;
    height: 145px;
    border-radius: 50%;
    background: var(--card);
}

.donut-center { position: relative; z-index: 1; text-align: center; }
.donut-center strong { font-size: 24px; display: block; }
.donut-center small { color: var(--muted); }

/* FORMS */
.field { margin-bottom: 17px; }

.field label {
    display: block;
    font-size: 13px;
    font-weight: bold;
    margin-bottom: 8px;
}

.field input, .field select {
    width: 100%;
    min-height: 47px;
    border: 1px solid var(--border);
    border-radius: 11px;
    padding: 10px 13px;
    outline: none;
    background: white;
    color: var(--green);
}

.field input:focus, .field select:focus { border-color: var(--green2); }

.form-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 15px;
}

.detail-value { font-size: 27px; font-weight: bold; margin: 10px 0; }

.alert-card {
    display: flex;
    align-items: flex-start;
    gap: 15px;
    background: var(--card);
    border: 1px solid var(--border);
    padding: 18px;
    border-radius: 15px;
    margin-bottom: 12px;
}

.alert-icon {
    width: 42px;
    height: 42px;
    flex-shrink: 0;
    border-radius: 12px;
    background: var(--soft);
    display: grid;
    place-items: center;
    font-size: 21px;
}

.alert-card p { color: var(--muted); font-size: 13px; margin-top: 6px; line-height: 1.5; }

.empty-state { text-align: center; padding: 35px 15px; color: var(--muted); }
.empty-state span { font-size: 40px; display: block; margin-bottom: 12px; }

.mobile-menu {
    display: none;
    border: 1px solid var(--border);
    background: white;
    padding: 9px 12px;
    border-radius: 10px;
    font-size: 20px;
}

/* PASSWORD RESET MODAL */
.reset-modal {
    position: fixed;
    inset: 0;
    z-index: 1000;
    background: #10251dcc;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 20px;
}

.reset-modal.hidden { display: none !important; }

.reset-box {
    width: 100%;
    max-width: 440px;
    background: var(--card);
    border-radius: 22px;
    padding: 28px;
    box-shadow: 0 15px 50px #0003;
}

.reset-box h2 { margin-bottom: 9px; }
.reset-box p { color: var(--muted); line-height: 1.5; margin-bottom: 20px; }
.reset-box .field { margin-bottom: 14px; }

.reset-close {
    float: right;
    border: 0;
    background: transparent;
    font-size: 25px;
    color: var(--green);
}

.reset-box .main-btn { margin-top: 5px; }

/* RESPONSIVE */
@media(max-width: 1100px) {
    .stats-grid { grid-template-columns: repeat(2, 1fr); }
    .device-grid { grid-template-columns: repeat(2, 1fr); }
    .main-area { padding: 28px 25px; }
}

@media(max-width: 850px) {
    .auth-container { grid-template-columns: 1fr; max-width: 480px; }
    .phone { min-height: 780px; }
    .sidebar { transform: translateX(-100%); transition: .3s; }
    .sidebar.open { transform: translateX(0); }
    .main-area { margin-left: 0; padding: 22px 18px; }
    .mobile-menu { display: block; }
    .two-columns, .map-layout { grid-template-columns: 1fr; }
}

@media(max-width: 520px) {
    .stats-grid, .device-grid, .form-grid { grid-template-columns: 1fr; }
    .topbar h1 { font-size: 23px; }
    .date-label { display: none; }
    .welcome-banner { padding: 23px 20px; }
    .welcome-banner::after { right: 10px; font-size: 65px; }
    .phone { padding: 25px 23px; }
    .logo { margin-top: 60px; }
}
</style>
</head>

<body>

<!-- AUTHENTICATION -->

<div class="auth-wrapper" id="authWrapper">
<div class="auth-container">

<section class="phone login" id="login">

    <div class="logo">
        <div class="logo-icon">⌂🌿</div>
        <h1>Energy <span>Watch</span></h1>
        <p class="tagline">Monitor • Save • Live Green</p>
    </div>

    <div class="city"></div>

    <form class="auth-form" onsubmit="loginUser(event)">
        <div class="input-box">
            <span class="icon">👤</span>
            <input type="email" id="loginEmail" placeholder="Email Address" required>
        </div>

        <div class="input-box">
            <span class="icon">🔒</span>
            <input type="password" id="loginPassword" placeholder="Password" required>
            <span class="eye" onclick="togglePassword('loginPassword',this)">◉</span>
        </div>

        <div class="options">
            <label class="remember">
                <input type="checkbox" id="rememberMe">
                Remember Me
            </label>
            <a onclick="forgotPassword()">Forgot Password?</a>
        </div>

        <button class="main-btn" id="loginButton" type="submit">Log In →</button>
    </form>

    <div class="divider">OR</div>

    <button class="google-btn" onclick="googleLogin()">
        <span class="google-icon">G</span>
        Continue with Google
    </button>

    <p class="bottom-text">
        Don't have an account?
        <a onclick="showSignup()">Sign Up</a>
    </p>

    <div class="decoration"></div>
</section>

<section class="phone signup" id="signup">
    <div class="top">
        <button class="back" onclick="showLogin()">←</button>
        <h2>Create Your Account</h2>
        <p class="subtitle">
            Join Energy Watch and start<br>
            managing your energy smarter!
        </p>
    </div>

    <form class="auth-form" onsubmit="signupUser(event)">
        <div class="input-box">
            <span class="icon">👤</span>
            <input type="text" id="signupName" placeholder="Full Name" required>
        </div>

        <div class="input-box">
            <span class="icon">✉</span>
            <input type="email" id="signupEmail" placeholder="Email Address" required>
        </div>

        <div class="input-box">
            <span class="icon">🔒</span>
            <input type="password" id="signupPassword" placeholder="Password" required minlength="8">
            <span class="eye" onclick="togglePassword('signupPassword',this)">◉</span>
        </div>

        <div class="input-box">
            <span class="icon">🔒</span>
            <input type="password" id="confirmPassword" placeholder="Confirm Password" required minlength="8">
            <span class="eye" onclick="togglePassword('confirmPassword',this)">◉</span>
        </div>

        <button class="main-btn" id="signupButton" type="submit">Create Account</button>
    </form>

    <div class="divider">OR</div>

    <button class="google-btn" onclick="googleLogin()">
        <span class="google-icon">G</span>
        Continue with Google
    </button>

    <p class="bottom-text">
        Already have an account?
        <a onclick="showLogin()">Log In</a>
    </p>

    <div class="decoration"></div>
</section>

</div>
</div>

<!-- PASSWORD RESET -->
<div class="reset-modal hidden" id="resetModal">
    <div class="reset-box">
        <button class="reset-close" onclick="closeResetModal()">×</button>
        <h2>Reset Password</h2>
        <p>Enter your email address. We will send you a verification code.</p>

        <div id="resetStepEmail">
            <div class="field">
                <label>Email Address</label>
                <input type="email" id="resetEmail" placeholder="Enter your email">
            </div>
            <button class="main-btn" id="sendCodeButton" onclick="sendResetCode()">Send Code</button>
        </div>

        <div id="resetStepCode" class="hidden">
            <div class="field">
                <label>Verification Code</label>
                <input type="text" id="resetCode" maxlength="6" placeholder="Enter 6-digit code">
            </div>
            <div class="field">
                <label>New Password</label>
                <input type="password" id="newResetPassword" minlength="8" placeholder="New password">
            </div>
            <div class="field">
                <label>Confirm New Password</label>
                <input type="password" id="confirmResetPassword" minlength="8" placeholder="Repeat new password">
            </div>
            <button class="main-btn" id="changeResetPasswordButton" onclick="changePasswordWithCode()">Change Password</button>
        </div>
    </div>
</div>

<!-- MAIN DASHBOARD -->

<div id="dashboard">

<aside class="sidebar" id="sidebar">
    <div class="side-logo">Energy <span>Watch</span> 🌿</div>

    <div class="nav-title">MAIN MENU</div>

    <div class="nav-link active" onclick="showPage('home',this)">
        <span class="nav-icon">⌂</span> Home
    </div>

    <div class="nav-link" onclick="showPage('devices',this)">
        <span class="nav-icon">▣</span> Devices
    </div>

    <div class="nav-link" onclick="showPage('energyMap',this)">
        <span class="nav-icon">◉</span> Energy Map
    </div>

    <div class="nav-link" onclick="showPage('budget',this)">
        <span class="nav-icon">▤</span> Budget Planner
    </div>

    <div class="nav-link" onclick="showPage('alerts',this)">
        <span class="nav-icon">♧</span> Alerts
    </div>

    <div class="sidebar-bottom">
        <div class="nav-title">ACCOUNT</div>
        <div class="nav-link" onclick="logoutUser()">
            <span class="nav-icon">↪</span> Log Out
        </div>

        <div class="user-mini">
            <div class="avatar" id="userAvatar">U</div>
            <div>
                <strong id="userName">User</strong>
                <small id="userEmail">user@email.com</small>
            </div>
        </div>
    </div>
</aside>

<main class="main-area">

    <header class="topbar">
        <div style="display:flex;align-items:center;gap:13px;">
            <button class="mobile-menu" onclick="toggleSidebar()">☰</button>
            <div>
                <h1 id="pageTitle">Dashboard</h1>
                <p id="pageSubtitle">Your energy overview</p>
            </div>
        </div>
        <div class="top-actions">
            <div class="date-label" id="todayDate"></div>
        </div>
    </header>

    <!-- HOME -->
    <section class="content-section active" id="home">

        <div class="welcome-banner">
            <h2 id="welcomeMessage">Welcome to Energy Watch!</h2>
            <p>
                Monitor your electricity consumption, understand your
                energy habits, and make smarter decisions every day.
            </p>
        </div>

        <div class="stats-grid">
            <div class="stat-card">
                <div class="stat-icon">⚡</div>
                <p>Daily Energy Usage</p>
                <h2 id="dailyUsage">0 kWh</h2>
                <small>Actual sensor reading</small>
            </div>

            <div class="stat-card">
                <div class="stat-icon">💰</div>
                <p>Monthly Electricity Cost</p>
                <h2 id="monthlyCost">0 EGP</h2>
                <small>Based on actual sensor reading</small>
            </div>

            <div class="stat-card">
                <div class="stat-icon">🔌</div>
                <p>My Devices</p>
                <h2 id="deviceCount">0</h2>
                <small>Devices added to your account</small>
            </div>

            <div class="stat-card">
                <div class="stat-icon">🟢</div>
                <p>Active Devices</p>
                <h2 id="activeCount">0</h2>
                <small>Devices marked as active</small>
            </div>
        </div>

        <div class="two-columns">
            <div class="panel">
                <h3>Energy Usage</h3>
                <p class="panel-subtitle">Actual readings from your sensor</p>
                <div class="detail-value" id="homeActualEnergy">0 kWh</div>
                <div class="progress-track">
                    <div class="progress-fill" id="homeEnergyProgress" style="width:0%"></div>
                </div>
                <div class="budget-line">
                    <span>Daily consumption</span>
                    <strong id="homeEnergyStatus">Waiting for sensor</strong>
                </div>
            </div>

            <div class="panel">
                <h3>Sensor Status</h3>
                <p class="panel-subtitle">Your Energy Watch hardware connection</p>
                <div class="detail-value" id="sensorStatus">Not Connected</div>
                <p class="panel-subtitle" id="sensorMessage">
                    Connect your sensor to start receiving actual readings.
                </p>
            </div>
        </div>

        <div class="section-heading">
            <h2>My Devices</h2>
            <button class="small-btn" onclick="showPageById('devices')">Manage Devices →</button>
        </div>

        <div class="device-grid" id="homeDeviceGrid"></div>
    </section>

    <!-- DEVICES -->
    <section class="content-section" id="devices">
        <div class="section-heading">
            <h2>My Devices</h2>
            <button class="small-btn" onclick="showAddDeviceForm()">+ Add Device</button>
        </div>

        <div class="panel hidden" id="addDevicePanel">
            <h3>Add New Device</h3>
            <p class="panel-subtitle">Add an appliance to your Energy Watch account</p>

            <form onsubmit="addDevice(event)">
                <div class="form-grid">
                    <div class="field">
                        <label>Device Name</label>
                        <input type="text" id="deviceName" placeholder="Example: Living Room AC" required>
                    </div>

                    <div class="field">
                        <label>Device Type</label>
                        <select id="deviceType" required>
                            <option value="ac">Air Conditioner</option>
                            <option value="fridge">Refrigerator</option>
                            <option value="heater">Water Heater</option>
                            <option value="washing">Washing Machine</option>
                            <option value="lighting">Lighting</option>
                            <option value="other">Other</option>
                        </select>
                    </div>

                    <div class="field">
                        <label>Power (Watts)</label>
                        <input type="number" id="deviceWatts" min="1" placeholder="Example: 1500" required>
                    </div>

                    <div class="field">
                        <label>Expected Operating Hours Per Day</label>
                        <input type="number" id="deviceHours" min="0" max="24" step="0.5" placeholder="Example: 3" required>
                    </div>
                </div>

                <button class="main-btn" type="submit">Save Device</button>
                <button class="outline-btn" type="button" onclick="hideAddDeviceForm()" style="margin-top:10px;width:100%">Cancel</button>
            </form>
        </div>

        <div class="device-grid" id="allDeviceGrid"></div>
    </section>

    <!-- DEVICE DETAILS -->
    <section class="content-section" id="details">
        <div class="section-heading">
            <h2 id="detailsDeviceName">Device Details</h2>
            <button class="outline-btn" onclick="showPageById('devices')">← Back to Devices</button>
        </div>

        <div class="panel">
            <form onsubmit="saveDeviceDetails(event)">
                <div class="form-grid">
                    <div class="field">
                        <label>Device Name</label>
                        <input id="editDeviceName" required>
                    </div>
                    <div class="field">
                        <label>Device Type</label>
                        <select id="editDeviceType">
                            <option value="ac">Air Conditioner</option>
                            <option value="fridge">Refrigerator</option>
                            <option value="heater">Water Heater</option>
                            <option value="washing">Washing Machine</option>
                            <option value="lighting">Lighting</option>
                            <option value="other">Other</option>
                        </select>
                    </div>
                    <div class="field">
                        <label>Power (Watts)</label>
                        <input type="number" id="editDeviceWatts" min="1" required>
                    </div>
                    <div class="field">
                        <label>Expected Hours Per Day</label>
                        <input type="number" id="editDeviceHours" min="0" max="24" step="0.5" required>
                    </div>
                </div>

                <button class="main-btn" type="submit">Save Changes</button>
            </form>

            <div class="section-heading">
                <h2>Actual Sensor Reading</h2>
            </div>
            <p class="panel-subtitle" id="deviceActualReading">
                0 kWh — Waiting for sensor data.
            </p>
        </div>
    </section>

    <!-- ENERGY MAP -->
    <section class="content-section" id="energyMap">
        <div class="section-heading">
            <h2>Energy Map</h2>
        </div>

        <div class="panel" style="margin-bottom:20px">
            <h3>Set Your Target Monthly Electricity Bill</h3>
            <p class="panel-subtitle">
                Enter the amount you want your monthly electricity bill to be.
                Energy Watch will estimate recommended operating hours for your devices.
            </p>

            <form onsubmit="saveTargetBill(event)">
                <div class="field">
                    <label>Target Monthly Bill (EGP)</label>
                    <input type="number" id="targetBillInput" min="1" step="0.01" placeholder="Enter your target bill" required>
                </div>
                <button class="main-btn" type="submit">Calculate My Energy Plan</button>
            </form>
        </div>

        <div class="map-layout">
            <div class="panel">
                <h3>Target Energy Distribution</h3>
                <p class="panel-subtitle">Estimated plan — not actual sensor readings</p>

                <div class="donut-area">
                    <div class="donut" id="energyDonut">
                        <div class="donut-center">
                            <strong id="targetDailyKwh">0 kWh</strong>
                            <small>Daily target</small>
                        </div>
                    </div>
                </div>
            </div>

            <div class="panel">
                <h3>Recommended Device Hours</h3>
                <p class="panel-subtitle">Suggested daily operating time based on your target bill</p>
                <div class="energy-list" id="energyPlanList"></div>
            </div>
        </div>

        <div class="panel" style="margin-top:20px">
            <h3>Plan Information</h3>
            <p class="panel-subtitle" id="energyPlanMessage">
                Enter a target bill and set the electricity price in Budget Planner to calculate your plan.
            </p>
        </div>
    </section>

    <!-- BUDGET -->
    <section class="content-section" id="budget">
        <div class="section-heading">
            <h2>Budget Planner</h2>
        </div>

        <div class="two-columns">
            <div class="panel">
                <h3>Electricity Price Settings</h3>
                <p class="panel-subtitle">Enter your electricity price per kWh and monthly budget.</p>

                <form onsubmit="saveBudget(event)">
                    <div class="field">
                        <label>Monthly Budget (EGP)</label>
                        <input type="number" id="budgetInput" min="0" step="0.01" required>
                    </div>

                    <div class="field">
                        <label>Price Per kWh (EGP)</label>
                        <input type="number" id="priceInput" min="0" step="0.01" required>
                    </div>

                    <button class="main-btn" type="submit">Save Budget Settings</button>
                </form>
            </div>

            <div class="panel">
                <h3>Actual Monthly Cost</h3>
                <p class="panel-subtitle">Calculated only from actual sensor readings</p>
                <div class="detail-value" id="budgetActualCost">0 EGP</div>
                <div class="progress-track">
                    <div class="progress-fill" id="budgetProgress" style="width:0%"></div>
                </div>
                <div class="budget-line">
                    <span>Monthly budget</span>
                    <strong id="budgetLimit">0 EGP</strong>
                </div>
            </div>
        </div>
    </section>

    <!-- ALERTS -->
    <section class="content-section" id="alerts">
        <div class="section-heading">
            <h2>Alerts</h2>
        </div>
        <div id="alertsList"></div>
    </section>

</main>
</div>

<script>
function togglePassword(id, element) {
    const input = document.getElementById(id);
    if (input.type === "password") {
        input.type = "text";
        element.textContent = "◎";
    } else {
        input.type = "password";
        element.textContent = "◉";
    }
}

function showSignup() {
    document.getElementById("login").style.display = "none";
    document.getElementById("signup").style.display = "flex";
}

function showLogin() {
    document.getElementById("signup").style.display = "none";
    document.getElementById("login").style.display = "flex";
}

function toggleSidebar() {
    document.getElementById("sidebar").classList.toggle("open");
}

function showPage(page, element) {
    document.querySelectorAll(".content-section").forEach(section => {
        section.classList.remove("active");
    });

    const target = document.getElementById(page);
    if (target) target.classList.add("active");

    document.querySelectorAll(".nav-link").forEach(link => {
        link.classList.remove("active");
    });

    if (element) {
        element.classList.add("active");
    } else {
        const links = document.querySelectorAll(".nav-link");
        const pageOrder = ["home", "devices", "energyMap", "budget", "alerts"];
        const index = pageOrder.indexOf(page);
        if (index >= 0 && links[index]) links[index].classList.add("active");
    }

    const titles = {
        home: ["Dashboard", "Your energy overview"],
        devices: ["My Devices", "Manage your appliances"],
        details: ["Device Details", "View and update device information"],
        energyMap: ["Energy Map", "Plan your target electricity bill"],
        budget: ["Budget Planner", "Manage your electricity budget"],
        alerts: ["Alerts", "Stay updated on your energy usage"]
    };

    document.getElementById("pageTitle").textContent = titles[page][0];
    document.getElementById("pageSubtitle").textContent = titles[page][1];
    document.getElementById("sidebar").classList.remove("open");
}

function showPageById(page) {
    showPage(page, null);
}

document.getElementById("todayDate").textContent =
    new Date().toLocaleDateString("en-US", {
        weekday: "short",
        month: "short",
        day: "numeric",
        year: "numeric"
    });
</script>

<script type="module">
import { initializeApp } from "https://www.gstatic.com/firebasejs/13.4.0/firebase-app.js";

import {
    getAuth,
    createUserWithEmailAndPassword,
    signInWithEmailAndPassword,
    updateProfile,
    GoogleAuthProvider,
    signInWithPopup,
    onAuthStateChanged,
    signOut
} from "https://www.gstatic.com/firebasejs/13.4.0/firebase-auth.js";

import {
    getDatabase,
    ref,
    set,
    get
} from "https://www.gstatic.com/firebasejs/13.4.0/firebase-database.js";

import {
    getFunctions,
    httpsCallable
} from "https://www.gstatic.com/firebasejs/13.4.0/firebase-functions.js";

/* FIREBASE CONFIG */

const firebaseConfig = {
    apiKey: "AIzaSyAF7VTwMd9AX98Qj_g2OcUmiJKZkvNU6jE",
    authDomain: "energy-watch-5100c.firebaseapp.com",
    databaseURL: "https://energy-watch-5100c-default-rtdb.europe-west1.firebasedatabase.app",
    projectId: "energy-watch-5100c",
    storageBucket: "energy-watch-5100c.firebasestorage.app",
    messagingSenderId: "147418632391",
    appId: "1:147418632391:web:4a2393d49ec78efa662ee2",
    measurementId: "G-5S50C2EGMK"
};

const app = initializeApp(firebaseConfig);
const auth = getAuth(app);
const db = getDatabase(app);
const functions = getFunctions(app, "europe-west1");

const requestPasswordCode = httpsCallable(functions, "requestPasswordCode");
const verifyPasswordCode = httpsCallable(functions, "verifyPasswordCode");

const googleProvider = new GoogleAuthProvider();
googleProvider.setCustomParameters({ prompt: "select_account" });

let currentUser = null;
let appData = null;
let selectedDeviceId = null;

const defaultData = {
    settings: {
        monthlyBudget: 0,
        pricePerKwh: 0,
        targetMonthlyBill: 0
    },
    devices: {},
    sensor: {
        connected: false,
        actualDailyKwh: 0,
        actualMonthlyKwh: 0,
        deviceReadings: {}
    }
};

const icons = {
    ac: "❄️",
    fridge: "🧊",
    heater: "🚿",
    washing: "🧺",
    lighting: "💡",
    other: "🔌"
};

function money(value) {
    return Number(value || 0).toLocaleString("en-US", {
        maximumFractionDigits: 2
    }) + " EGP";
}

function escapeHTML(value) {
    return String(value ?? "").replace(/[&<>"']/g, character => ({
        "&": "&amp;",
        "<": "&lt;",
        ">": "&gt;",
        '"': "&quot;",
        "'": "&#39;"
    }[character]));
}

function getDevices() {
    return Object.entries(appData?.devices || {}).map(([id, device]) => ({
        id,
        ...device
    }));
}

function sensorConnected() {
    return appData?.sensor?.connected === true;
}

function actualDaily() {
    if (!sensorConnected()) return 0;
    return Number(appData.sensor.actualDailyKwh || 0);
}

function actualMonthly() {
    if (!sensorConnected()) return 0;
    return Number(appData.sensor.actualMonthlyKwh || 0);
}

function actualCost() {
    return actualMonthly() * Number(appData?.settings?.pricePerKwh || 0);
}

async function saveAppData() {
    if (!currentUser) throw new Error("No signed-in user.");
    await set(ref(db, `users/${currentUser.uid}/energyWatch`), appData);
}

function showDashboard() {
    document.getElementById("authWrapper").style.display = "none";
    document.getElementById("dashboard").style.display = "block";
}

function showAuth() {
    document.getElementById("dashboard").style.display = "none";
    document.getElementById("authWrapper").style.display = "flex";
}

function mergeDefaults(savedData) {
    const merged = {
        ...structuredClone(defaultData),
        ...(savedData || {})
    };

    merged.settings = {
        ...defaultData.settings,
        ...(savedData?.settings || {})
    };

    merged.devices = savedData?.devices || {};

    merged.sensor = {
        ...defaultData.sensor,
        ...(savedData?.sensor || {}),
        deviceReadings: savedData?.sensor?.deviceReadings || {}
    };

    return merged;
}

/* SIGN UP */

window.signupUser = async function(event) {
    event.preventDefault();

    const button = document.getElementById("signupButton");
    const name = document.getElementById("signupName").value.trim();
    const email = document.getElementById("signupEmail").value.trim();
    const password = document.getElementById("signupPassword").value;
    const confirm = document.getElementById("confirmPassword").value;

    if (password.length < 8) {
        alert("Password must be at least 8 characters.");
        return;
    }

    if (password !== confirm) {
        alert("Passwords do not match.");
        return;
    }

    button.disabled = true;
    button.textContent = "Creating account...";

    try {
        const result = await createUserWithEmailAndPassword(auth, email, password);
        await updateProfile(result.user, { displayName: name });
        alert("Your account has been created successfully!");
    } catch (error) {
        console.error(error);
        alert("Sign Up Error: " + error.message);
    } finally {
        button.disabled = false;
        button.textContent = "Create Account";
    }
};

/* LOGIN */

window.loginUser = async function(event) {
    event.preventDefault();

    const button = document.getElementById("loginButton");
    const email = document.getElementById("loginEmail").value.trim();
    const password = document.getElementById("loginPassword").value;

    button.disabled = true;
    button.textContent = "Logging in...";

    try {
        await signInWithEmailAndPassword(auth, email, password);
    } catch (error) {
        console.error(error);
        alert("Login Error: " + error.message);
    } finally {
        button.disabled = false;
        button.textContent = "Log In →";
    }
};

/* GOOGLE LOGIN */

window.googleLogin = async function() {
    try {
        await signInWithPopup(auth, googleProvider);
    } catch (error) {
        console.error(error);
        alert("Google Login Error: " + error.message);
    }
};

/* FORGOT PASSWORD */

window.forgotPassword = function() {
    const email = document.getElementById("loginEmail").value.trim();

    document.getElementById("resetModal").classList.remove("hidden");
    document.getElementById("resetStepEmail").classList.remove("hidden");
    document.getElementById("resetStepCode").classList.add("hidden");

    if (email) {
        document.getElementById("resetEmail").value = email;
    }
};

window.closeResetModal = function() {
    document.getElementById("resetModal").classList.add("hidden");
};

window.sendResetCode = async function() {
    const email = document.getElementById("resetEmail").value.trim();
    const button = document.getElementById("sendCodeButton");

    if (!email) {
        alert("Please enter your email address.");
        return;
    }

    button.disabled = true;
    button.textContent = "Sending...";

    try {
        await requestPasswordCode({ email });

        document.getElementById("resetStepEmail").classList.add("hidden");
        document.getElementById("resetStepCode").classList.remove("hidden");

        alert("If the account exists, a verification code has been sent to your email.");
    } catch (error) {
        console.error(error);
        alert("Could not send verification code. Please check your server function and try again.");
    } finally {
        button.disabled = false;
        button.textContent = "Send Code";
    }
};

window.changePasswordWithCode = async function() {
    const email = document.getElementById("resetEmail").value.trim();
    const code = document.getElementById("resetCode").value.trim();
    const newPassword = document.getElementById("newResetPassword").value;
    const confirmPassword = document.getElementById("confirmResetPassword").value;
    const button = document.getElementById("changeResetPasswordButton");

    if (!/^\d{6}$/.test(code)) {
        alert("Please enter the 6-digit verification code.");
        return;
    }

    if (newPassword.length < 8) {
        alert("Password must be at least 8 characters.");
        return;
    }

    if (newPassword !== confirmPassword) {
        alert("Passwords do not match.");
        return;
    }

    button.disabled = true;
    button.textContent = "Changing Password...";

    try {
        await verifyPasswordCode({
            email,
            code,
            newPassword
        });

        alert("Your password has been changed successfully!");
        closeResetModal();
        showLogin();

        document.getElementById("loginEmail").value = email;
        document.getElementById("loginPassword").value = "";
    } catch (error) {
        console.error(error);
        alert("Could not verify the code or change the password. Please check the code and try again.");
    } finally {
        button.disabled = false;
        button.textContent = "Change Password";
    }
};

/* LOGOUT */

window.logoutUser = async function() {
    try {
        await signOut(auth);
        currentUser = null;
        appData = null;
        showAuth();
    } catch (error) {
        console.error(error);
        alert("Logout Error: " + error.message);
    }
};

/* AUTH STATE */

onAuthStateChanged(auth, async user => {
    if (!user) {
        currentUser = null;
        appData = null;
        showAuth();
        return;
    }

    currentUser = user;

    try {
        const snapshot = await get(ref(db, `users/${user.uid}/energyWatch`));

        if (snapshot.exists()) {
            appData = mergeDefaults(snapshot.val());
        } else {
            appData = structuredClone(defaultData);
            await saveAppData();
        }

        document.getElementById("userName").textContent =
            user.displayName || "Energy Watch User";

        document.getElementById("userEmail").textContent = user.email || "";

        document.getElementById("userAvatar").textContent =
            (user.displayName || user.email || "U").charAt(0).toUpperCase();

        document.getElementById("welcomeMessage").textContent =
            `Welcome to Energy Watch${user.displayName ? ", " + user.displayName : "!"}`;

        showDashboard();
        renderEverything();
    } catch (error) {
        console.error(error);
        alert("Could not load your account data. Please check your internet connection.");
    }
});

/* HOME */

function renderHome() {
    const devices = getDevices();
    const activeDevices = devices.filter(device => device.active);

    document.getElementById("dailyUsage").textContent =
        actualDaily().toFixed(2) + " kWh";

    document.getElementById("monthlyCost").textContent =
        money(actualCost());

    document.getElementById("deviceCount").textContent = devices.length;
    document.getElementById("activeCount").textContent = activeDevices.length;

    document.getElementById("homeActualEnergy").textContent =
        actualDaily().toFixed(2) + " kWh";

    document.getElementById("homeEnergyProgress").style.width =
        Math.min(actualDaily() * 10, 100) + "%";

    document.getElementById("homeEnergyStatus").textContent =
        sensorConnected() ? "Sensor connected" : "Waiting for sensor";

    document.getElementById("sensorStatus").textContent =
        sensorConnected() ? "Connected" : "Not Connected";

    document.getElementById("sensorMessage").textContent =
        sensorConnected()
            ? "Your sensor is connected. Actual readings will appear here."
            : "Connect your sensor to start receiving actual readings.";

    const grid = document.getElementById("homeDeviceGrid");

    if (!devices.length) {
        grid.innerHTML = `
            <div class="panel empty-state" style="grid-column:1/-1">
                <span>🔌</span>
                <strong>No devices added yet</strong>
                <p>Add your first device to start planning your energy usage.</p>
            </div>`;
    } else {
        grid.innerHTML = devices.slice(0, 3).map(device => deviceCardHTML(device)).join("");
    }
}

/* DEVICE CARD */

function deviceCardHTML(device) {
    const icon = icons[device.type] || icons.other;
    const reading = sensorConnected()
        ? Number(appData.sensor.deviceReadings?.[device.id]?.dailyKwh || 0)
        : 0;

    return `
        <div class="device-card">
            <div class="device-top">
                <div class="device-emoji">${icon}</div>
                <span class="status ${device.active ? "" : "off"}">
                    ${device.active ? "Active" : "Off"}
                </span>
            </div>

            <h3>${escapeHTML(device.name)}</h3>
            <p>${escapeHTML(device.type || "Device")}</p>

            <div class="device-metrics">
                <span>${Number(device.watts || 0)} W</span>
                <span>${Number(device.hours || 0)} hrs/day</span>
            </div>

            <p style="margin-top:12px;margin-bottom:0">
                Actual reading: <strong>${reading.toFixed(2)} kWh</strong>
            </p>

            <div class="device-actions">
                <button onclick="toggleDevice('${escapeHTML(device.id)}')">
                    ${device.active ? "Turn Off" : "Turn On"}
                </button>
                <button onclick="openDeviceDetails('${escapeHTML(device.id)}')">
                    Details
                </button>
                <button class="delete-btn" onclick="deleteDevice('${escapeHTML(device.id)}')">
                    Delete
                </button>
            </div>
        </div>`;
}

/* DEVICES */

function renderDevices() {
    const devices = getDevices();
    const grid = document.getElementById("allDeviceGrid");

    if (!devices.length) {
        grid.innerHTML = `
            <div class="panel empty-state" style="grid-column:1/-1">
                <span>🔌</span>
                <strong>No devices added yet</strong>
                <p>Click "Add Device" to add your appliances.</p>
            </div>`;
        return;
    }

    grid.innerHTML = devices.map(device => deviceCardHTML(device)).join("");
}

window.showAddDeviceForm = function() {
    document.getElementById("addDevicePanel").classList.remove("hidden");
};

window.hideAddDeviceForm = function() {
    document.getElementById("addDevicePanel").classList.add("hidden");
};

window.addDevice = async function(event) {
    event.preventDefault();

    const name = document.getElementById("deviceName").value.trim();
    const type = document.getElementById("deviceType").value;
    const watts = Number(document.getElementById("deviceWatts").value);
    const hours = Number(document.getElementById("deviceHours").value);

    if (!name || watts <= 0 || hours < 0 || hours > 24) {
        alert("Please enter valid device information.");
        return;
    }

    const id = "device_" + Date.now();

    appData.devices[id] = {
        name,
        type,
        watts,
        hours,
        active: true
    };

    try {
        await saveAppData();
        document.querySelector("#addDevicePanel form").reset();
        hideAddDeviceForm();
        renderEverything();
        alert("Device added successfully!");
    } catch (error) {
        console.error(error);
        delete appData.devices[id];
        alert("Could not save this device. Please try again.");
    }
};

/* DELETE DEVICE */

window.deleteDevice = async function(id) {
    const device = appData.devices?.[id];

    if (!device) return;

    const confirmed = confirm(`Are you sure you want to delete "${device.name}"?`);
    if (!confirmed) return;

    const oldDevice = { ...device };
    delete appData.devices[id];

    try {
        await saveAppData();

        if (selectedDeviceId === id) {
            selectedDeviceId = null;
            showPageById("devices");
        }

        renderEverything();
        alert("Device deleted successfully!");
    } catch (error) {
        console.error(error);
        appData.devices[id] = oldDevice;
        renderEverything();
        alert("Could not delete this device. Please try again.");
    }
};

/* DEVICE ACTIONS */

window.toggleDevice = async function(id) {
    const device = appData.devices?.[id];
    if (!device) return;

    device.active = !device.active;

    try {
        await saveAppData();
        renderEverything();
    } catch (error) {
        console.error(error);
        device.active = !device.active;
        renderEverything();
        alert("Could not update device status.");
    }
};

window.openDeviceDetails = function(id) {
    const device = appData.devices?.[id];
    if (!device) return;

    selectedDeviceId = id;

    document.getElementById("detailsDeviceName").textContent = device.name;
    document.getElementById("editDeviceName").value = device.name || "";
    document.getElementById("editDeviceType").value = device.type || "other";
    document.getElementById("editDeviceWatts").value = device.watts || 0;
    document.getElementById("editDeviceHours").value = device.hours || 0;

    const reading = sensorConnected()
        ? Number(appData.sensor.deviceReadings?.[id]?.dailyKwh || 0)
        : 0;

    document.getElementById("deviceActualReading").textContent =
        `${reading.toFixed(2)} kWh — ${sensorConnected() ? "Actual sensor reading" : "Waiting for sensor data."}`;

    showPageById("details");
};

window.saveDeviceDetails = async function(event) {
    event.preventDefault();

    if (!selectedDeviceId || !appData.devices[selectedDeviceId]) return;

    const device = appData.devices[selectedDeviceId];

    const oldDevice = { ...device };

    device.name = document.getElementById("editDeviceName").value.trim();
    device.type = document.getElementById("editDeviceType").value;
    device.watts = Number(document.getElementById("editDeviceWatts").value);
    device.hours = Number(document.getElementById("editDeviceHours").value);

    if (!device.name || device.watts <= 0 || device.hours < 0 || device.hours > 24) {
        Object.assign(device, oldDevice);
        alert("Please enter valid device information.");
        return;
    }

    try {
        await saveAppData();
        renderEverything();
        alert("Device details updated successfully!");
    } catch (error) {
        console.error(error);
        Object.assign(device, oldDevice);
        alert("Could not update device details.");
    }
};

/* ENERGY MAP PLAN */

function calculateEnergyPlan() {
    const devices = getDevices();
    const targetBill = Number(appData.settings.targetMonthlyBill || 0);
    const price = Number(appData.settings.pricePerKwh || 0);

    const list = document.getElementById("energyPlanList");
    const message = document.getElementById("energyPlanMessage");

    document.getElementById("targetBillInput").value = targetBill || "";

    if (!targetBill) {
        document.getElementById("targetDailyKwh").textContent = "0 kWh";
        document.getElementById("energyDonut").style.background =
            "conic-gradient(#e4e8df 0deg 360deg)";
        list.innerHTML = `<div class="empty-state">Enter your target monthly bill to calculate a plan.</div>`;
        message.textContent = "Enter a target bill and set the electricity price in Budget Planner.";
        return;
    }

    if (price <= 0) {
        document.getElementById("targetDailyKwh").textContent = "—";
        list.innerHTML = `<div class="empty-state">Please enter the electricity price per kWh in Budget Planner first.</div>`;
        message.textContent = "The price per kWh is currently 0. Add the price in Budget Planner to calculate the target energy.";
        return;
    }

    const dailyTargetKwh = targetBill / price / 30;

    document.getElementById("targetDailyKwh").textContent =
        dailyTargetKwh.toFixed(2) + " kWh";

    if (!devices.length) {
        list.innerHTML = `<div class="empty-state">Add devices first to calculate recommended operating hours.</div>`;
        message.textContent =
            `Your target bill of ${money(targetBill)} equals approximately ${dailyTargetKwh.toFixed(2)} kWh per day. Add your devices to divide this target between them.`;
        return;
    }

    const baseline = devices.map(device => ({
        ...device,
        baselineKwh: (Number(device.watts || 0) * Number(device.hours || 0)) / 1000
    }));

    let totalBaseline = baseline.reduce((sum, device) => sum + device.baselineKwh, 0);

    if (totalBaseline <= 0) {
        totalBaseline = baseline.reduce((sum, device) => sum + Math.max(Number(device.watts || 0), 0), 0);
    }

    if (totalBaseline <= 0) {
        list.innerHTML = `<div class="empty-state">Please check the power values of your devices.</div>`;
        return;
    }

    let colors = ["#315d42", "#8dbd5d", "#b7c9a7", "#dce6d1", "#9aaa84", "#567b5b"];
    let gradientParts = [];
    let currentDegree = 0;

    const plan = baseline.map((device, index) => {
        const weight = device.baselineKwh > 0
            ? device.baselineKwh
            : (totalBaseline / devices.length);

        const share = device.baselineKwh > 0
            ? weight / totalBaseline
            : (1 / devices.length);

        const allocatedKwh = dailyTargetKwh * share;
        const watts = Number(device.watts || 0);
        const recommendedHours = watts > 0
            ? Math.min(24, (allocatedKwh * 1000) / watts)
            : 0;

        const degrees = share * 360;
        gradientParts.push(`${colors[index % colors.length]} ${currentDegree}deg ${currentDegree + degrees}deg`);
        currentDegree += degrees;

        return {
            ...device,
            share,
            allocatedKwh,
            recommendedHours
        };
    });

    document.getElementById("energyDonut").style.background =
        `conic-gradient(${gradientParts.join(",")})`;

    list.innerHTML = plan.map((device, index) => `
        <div class="energy-item">
            <div class="energy-emoji">${icons[device.type] || icons.other}</div>
            <div>
                <strong>${escapeHTML(device.name)}</strong>
                <small>${device.allocatedKwh.toFixed(2)} kWh/day · ${(device.share * 100).toFixed(1)}% of target</small>
                <div class="progress-track">
                    <div class="progress-fill" style="width:${Math.min(device.share * 100, 100)}%"></div>
                </div>
            </div>
            <strong>${device.recommendedHours.toFixed(1)} hrs</strong>
        </div>
    `).join("");

    const exceeds = plan.some(device => {
        const rawHours = device.watts > 0
            ? (device.allocatedKwh * 1000) / device.watts
            : 0;
        return rawHours > 24;
    });

    message.textContent =
        `Your target bill of ${money(targetBill)} allows approximately ${dailyTargetKwh.toFixed(2)} kWh per day, using ${money(price)} per kWh. These are planning estimates, not actual sensor readings.` +
        (exceeds ? " Some devices would need more than 24 hours per day at the current power settings. Review your device values or target bill." : "");
}

window.saveTargetBill = async function(event) {
    event.preventDefault();

    const targetBill = Number(document.getElementById("targetBillInput").value);

    if (!Number.isFinite(targetBill) || targetBill <= 0) {
        alert("Please enter a target monthly bill greater than 0.");
        return;
    }

    appData.settings.targetMonthlyBill = targetBill;

    try {
        await saveAppData();
        renderEverything();
        alert("Your target monthly bill has been saved and the Energy Map plan updated.");
    } catch (error) {
        console.error(error);
        alert("Could not save your target bill. Please try again.");
    }
};

/* BUDGET */

function renderBudget() {
    document.getElementById("budgetInput").value =
        appData.settings.monthlyBudget || 0;

    document.getElementById("priceInput").value =
        appData.settings.pricePerKwh || 0;

    document.getElementById("budgetActualCost").textContent =
        money(actualCost());

    document.getElementById("budgetLimit").textContent =
        money(appData.settings.monthlyBudget || 0);

    const budget = Number(appData.settings.monthlyBudget || 0);
    const cost = actualCost();

    document.getElementById("budgetProgress").style.width =
        budget > 0 ? Math.min((cost / budget) * 100, 100) + "%" : "0%";
}

window.saveBudget = async function(event) {
    event.preventDefault();

    const budget = Number(document.getElementById("budgetInput").value);
    const price = Number(document.getElementById("priceInput").value);

    if (budget < 0 || price < 0) {
        alert("Please enter valid budget information.");
        return;
    }

    appData.settings.monthlyBudget = budget;
    appData.settings.pricePerKwh = price;

    try {
        await saveAppData();
        renderEverything();
        alert("Budget settings saved successfully!");
    } catch (error) {
        console.error(error);
        alert("Could not save your budget settings.");
    }
};

/* ALERTS */

function renderAlerts() {
    const alerts = document.getElementById("alertsList");

    if (!sensorConnected()) {
        alerts.innerHTML = `
            <div class="alert-card">
                <div class="alert-icon">ℹ️</div>
                <div>
                    <strong>Sensor not connected</strong>
                    <p>Actual electricity readings will appear after your sensor is connected and starts sending data.</p>
                </div>
            </div>`;
        return;
    }

    alerts.innerHTML = `
        <div class="alert-card">
            <div class="alert-icon">⚡</div>
            <div>
                <strong>Sensor connected</strong>
                <p>Your Energy Watch sensor is connected and actual readings are available.</p>
            </div>
        </div>`;
}

/* RENDER EVERYTHING */

function renderEverything() {
    if (!appData) return;

    renderHome();
    renderDevices();
    renderBudget();
    calculateEnergyPlan();
    renderAlerts();
}

</script>

</body>
</html>
