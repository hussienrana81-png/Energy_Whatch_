
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

button {
    cursor: pointer;
}

.hidden {
    display: none !important;
}

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

.phone > * {
    position: relative;
    z-index: 1;
}

.logo {
    text-align: center;
    margin-top: 90px;
}

.logo-icon {
    font-size: 85px;
    color: var(--green);
}

.logo h1 {
    font-size: 43px;
    letter-spacing: -2px;
    margin-top: 10px;
}

.logo h1 span {
    color: var(--light-green);
}

.tagline {
    margin-top: 12px;
    font-size: 18px;
}

.city {
    height: 120px;
    width: calc(100% + 80px);
    margin-top: 25px;
    background: linear-gradient(to top, #a8c69c, #edf2e7);
    clip-path: polygon(0 65%,12% 50%,22% 65%,35% 38%,50% 60%,63% 35%,77% 60%,90% 30%,100% 55%,100% 100%,0 100%);
}

.auth-form {
    width: 100%;
    margin-top: 20px;
}

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

.input-box .icon {
    font-size: 21px;
    margin-right: 15px;
}

.input-box input {
    width: 100%;
    border: none;
    outline: none;
    background: transparent;
    font-size: 16px;
    color: var(--green);
}

.eye {
    cursor: pointer;
    color: #777;
}

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

.main-btn:disabled,
.google-btn:disabled {
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

.remember {
    display: flex;
    align-items: center;
    gap: 7px;
}

.remember input {
    accent-color: var(--green);
}

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

.divider::before,
.divider::after {
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

.google-icon {
    color: #4285f4;
    font-weight: bold;
    margin-right: 10px;
}

.bottom-text {
    margin-top: 25px;
    text-align: center;
    color: #222;
}

.bottom-text a {
    margin-left: 5px;
}

.signup {
    display: none;
}

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

.signup h2 {
    font-size: 32px;
    margin-bottom: 12px;
}

.signup .subtitle {
    font-size: 16px;
    line-height: 1.5;
    color: #555;
}

.signup .auth-form {
    margin-top: 25px;
}

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

#dashboard {
    display: none;
    min-height: 100vh;
}

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

.side-logo span {
    color: #a4cf70;
}

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

.nav-link:hover,
.nav-link.active {
    background: #315d42;
    color: white;
}

.nav-link .nav-icon {
    font-size: 19px;
    width: 23px;
}

.sidebar-bottom {
    margin-top: auto;
}

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

.topbar h1 {
    font-size: 30px;
}

.topbar p {
    color: var(--muted);
    margin-top: 7px;
}

.top-actions {
    display: flex;
    gap: 10px;
    align-items: center;
}

.date-label {
    background: white;
    border: 1px solid var(--border);
    padding: 11px 15px;
    border-radius: 12px;
    color: #596354;
    font-size: 13px;
}

.content-section {
    display: none;
    animation: fadeIn .3s ease;
}

.content-section.active {
    display: block;
}

@keyframes fadeIn {
    from {opacity: 0; transform: translateY(8px);}
    to {opacity: 1; transform: translateY(0);}
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

.welcome-banner h2 {
    font-size: 25px;
    margin-bottom: 10px;
}

.welcome-banner p {
    color: #e1eadf;
    line-height: 1.6;
    max-width: 550px;
}

.stats-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 17px;
    margin-bottom: 25px;
}

.stat-card,
.panel,
.device-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 18px;
    padding: 22px;
    box-shadow: 0 5px 15px #00000005;
}

.stat-card {
    transition: .25s;
}

.stat-card:hover,
.device-card:hover {
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

.stat-card p {
    color: var(--muted);
    font-size: 13px;
}

.stat-card h2 {
    font-size: 25px;
    margin: 8px 0;
}

.stat-card small {
    color: var(--muted);
}

.two-columns {
    display: grid;
    grid-template-columns: 1.3fr 1fr;
    gap: 18px;
    margin-bottom: 22px;
}

.panel h3 {
    font-size: 18px;
    margin-bottom: 8px;
}

.panel-subtitle {
    color: var(--muted);
    font-size: 13px;
    margin-bottom: 20px;
}

.section-heading {
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 15px;
    margin: 28px 0 16px;
}

.section-heading h2 {
    font-size: 21px;
}

.small-btn {
    border: none;
    background: var(--green);
    color: white;
    padding: 11px 17px;
    border-radius: 12px;
    font-weight: bold;
}

.small-btn:hover {
    background: var(--green2);
}

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

.device-card {
    transition: .25s;
}

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

.status.off {
    background: #eeeeeb;
    color: #777;
}

.device-card h3 {
    margin-bottom: 7px;
    font-size: 17px;
}

.device-card p {
    color: var(--muted);
    font-size: 13px;
    margin-bottom: 15px;
}

.device-metrics {
    display: flex;
    justify-content: space-between;
    border-top: 1px solid var(--border);
    padding-top: 13px;
    font-size: 13px;
}

.device-actions {
    display: flex;
    gap: 8px;
    margin-top: 15px;
}

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

.device-actions button:hover {
    background: var(--soft);
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

.energy-list {
    display: flex;
    flex-direction: column;
    gap: 17px;
}

.energy-item {
    display: grid;
    grid-template-columns: 35px 1fr auto;
    gap: 10px;
    align-items: center;
}

.energy-item .energy-emoji {
    font-size: 21px;
}

.energy-item small {
    display: block;
    color: var(--muted);
    margin-top: 5px;
    font-size: 12px;
}

.energy-item strong {
    font-size: 13px;
}

.energy-item .progress-track {
    margin: 7px 0 0;
    height: 7px;
}

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

.donut-center {
    position: relative;
    z-index: 1;
    text-align: center;
}

.donut-center strong {
    font-size: 24px;
    display: block;
}

.donut-center small {
    color: var(--muted);
}

/* FORMS */

.field {
    margin-bottom: 17px;
}

.field label {
    display: block;
    font-size: 13px;
    font-weight: bold;
    margin-bottom: 8px;
}

.field input,
.field select {
    width: 100%;
    min-height: 47px;
    border: 1px solid var(--border);
    border-radius: 11px;
    padding: 10px 13px;
    outline: none;
    background: white;
    color: var(--green);
}

.field input:focus,
.field select:focus {
    border-color: var(--green2);
}

.form-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 15px;
}

.detail-value {
    font-size: 27px;
    font-weight: bold;
    margin: 10px 0;
}

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

.alert-card p {
    color: var(--muted);
    font-size: 13px;
    margin-top: 6px;
    line-height: 1.5;
}

.empty-state {
    text-align: center;
    padding: 35px 15px;
    color: var(--muted);
}

.empty-state span {
    font-size: 40px;
    display: block;
    margin-bottom: 12px;
}

.mobile-menu {
    display: none;
    border: 1px solid var(--border);
    background: white;
    padding: 9px 12px;
    border-radius: 10px;
    font-size: 20px;
}

/* RESPONSIVE */

@media(max-width: 1100px) {
    .stats-grid {
        grid-template-columns: repeat(2, 1fr);
    }

    .device-grid {
        grid-template-columns: repeat(2, 1fr);
    }

    .main-area {
        padding: 28px 25px;
    }
}

@media(max-width: 850px) {
    .auth-container {
        grid-template-columns: 1fr;
        max-width: 480px;
    }

    .phone {
        min-height: 780px;
    }

    .sidebar {
        transform: translateX(-100%);
        transition: .3s;
    }

    .sidebar.open {
        transform: translateX(0);
    }

    .main-area {
        margin-left: 0;
        padding: 22px 18px;
    }

    .mobile-menu {
        display: block;
    }

    .two-columns,
    .map-layout {
        grid-template-columns: 1fr;
    }
}

@media(max-width: 520px) {
    .stats-grid,
    .device-grid,
    .form-grid {
        grid-template-columns: 1fr;
    }

    .topbar h1 {
        font-size: 23px;
    }

    .date-label {
        display: none;
    }

    .welcome-banner {
        padding: 23px 20px;
    }

    .welcome-banner::after {
        right: 10px;
        font-size: 65px;
    }

    .phone {
        padding: 25px 23px;
    }

    .logo {
        margin-top: 60px;
    }
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
            <input type="password" id="signupPassword" placeholder="Password" required minlength="6">
            <span class="eye" onclick="togglePassword('signupPassword',this)">◉</span>
        </div>

        <div class="input-box">
            <span class="icon">🔒</span>
            <input type="password" id="confirmPassword" placeholder="Confirm Password" required minlength="6">
            <span class="eye" onclick="togglePassword('confirmPassword',this)">◉</span>
        </div>

        <button class="main-btn" id="signupButton" type="submit">Sign Up →</button>
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
                <small>Estimated daily consumption</small>
            </div>

            <div class="stat-card">
                <div class="stat-icon">💰</div>
                <p>Monthly Cost</p>
                <h2 id="monthlyCost">0 EGP</h2>
                <small>Estimated monthly cost</small>
            </div>

            <div class="stat-card">
                <div class="stat-icon">▣</div>
                <p>Connected Devices</p>
                <h2 id="deviceCount">0</h2>
                <small>Devices in your account</small>
            </div>

            <div class="stat-card">
                <div class="stat-icon">🌱</div>
                <p>Active Devices</p>
                <h2 id="activeCount">0</h2>
                <small>Currently marked as active</small>
            </div>

        </div>

        <div class="two-columns">

            <div class="panel">
                <h3>Energy Consumption</h3>
                <p class="panel-subtitle">Estimated daily energy by device</p>
                <div id="homeEnergyList" class="energy-list"></div>
            </div>

            <div class="panel">
                <h3>Monthly Budget</h3>
                <p class="panel-subtitle">Your estimated spending progress</p>

                <div class="detail-value" id="homeBudgetCost">0 EGP</div>

                <div class="progress-track">
                    <div class="progress-fill" id="homeBudgetProgress" style="width:0%"></div>
                </div>

                <div class="budget-line">
                    <span id="homeBudgetUsed">Used: 0 EGP</span>
                    <span id="homeBudgetLimit">Limit: 0 EGP</span>
                </div>

                <br>
                <button class="outline-btn" onclick="showPageById('budget')">
                    Manage Budget →
                </button>
            </div>

        </div>

        <div class="section-heading">
            <h2>Your Devices</h2>
            <button class="small-btn" onclick="showPageById('devices')">View All →</button>
        </div>

        <div class="device-grid" id="homeDeviceGrid"></div>

    </section>


    <!-- DEVICES -->

    <section class="content-section" id="devices">

        <div class="section-heading">
            <div>
                <h2>My Devices</h2>
                <p class="panel-subtitle">Manage your connected appliances</p>
            </div>
        </div>

        <div class="panel" style="margin-bottom:22px;">
            <h3>Add New Device</h3>
            <p class="panel-subtitle">Enter the device information to estimate its energy use.</p>

            <form onsubmit="addDevice(event)">

                <div class="form-grid">

                    <div class="field">
                        <label>Device Name</label>
                        <input type="text" id="newDeviceName" placeholder="Example: Air Conditioner" required>
                    </div>

                    <div class="field">
                        <label>Device Type</label>
                        <select id="newDeviceType">
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
                        <input type="number" id="newDeviceWatts" min="1" placeholder="Example: 1500" required>
                    </div>

                    <div class="field">
                        <label>Operating Hours Per Day</label>
                        <input type="number" id="newDeviceHours" min="0" max="24" step="0.5" placeholder="Example: 3" required>
                    </div>

                </div>

                <button class="small-btn" type="submit">+ Add Device</button>

            </form>
        </div>

        <div class="device-grid" id="allDeviceGrid"></div>

    </section>


    <!-- DEVICE DETAILS -->

    <section class="content-section" id="details">

        <button class="outline-btn" onclick="showPageById('devices')">← Back to Devices</button>

        <div class="section-heading">
            <div>
                <h2 id="detailName">Device Details</h2>
                <p class="panel-subtitle">Consumption and operating information</p>
            </div>
        </div>

        <div class="stats-grid" style="grid-template-columns:repeat(3,1fr);">

            <div class="stat-card">
                <div class="stat-icon">⚡</div>
                <p>Daily Consumption</p>
                <h2 id="detailDaily">0 kWh</h2>
            </div>

            <div class="stat-card">
                <div class="stat-icon">📅</div>
                <p>Monthly Consumption</p>
                <h2 id="detailMonthly">0 kWh</h2>
            </div>

            <div class="stat-card">
                <div class="stat-icon">💰</div>
                <p>Monthly Cost</p>
                <h2 id="detailCost">0 EGP</h2>
            </div>

        </div>

        <div class="panel">
            <h3>Update Device Information</h3>
            <p class="panel-subtitle">Change the estimated power and daily operating hours.</p>

            <form onsubmit="saveDeviceDetails(event)">

                <div class="form-grid">
                    <div class="field">
                        <label>Device Name</label>
                        <input type="text" id="editDeviceName" required>
                    </div>

                    <div class="field">
                        <label>Power (Watts)</label>
                        <input type="number" id="editDeviceWatts" min="1" required>
                    </div>

                    <div class="field">
                        <label>Operating Hours Per Day</label>
                        <input type="number" id="editDeviceHours" min="0" max="24" step="0.5" required>
                    </div>

                    <div class="field">
                        <label>Device Status</label>
                        <select id="editDeviceStatus">
                            <option value="true">Active</option>
                            <option value="false">Inactive</option>
                        </select>
                    </div>
                </div>

                <button class="small-btn" type="submit">Save Changes</button>
            </form>
        </div>

    </section>


    <!-- ENERGY MAP -->

    <section class="content-section" id="energyMap">

        <div class="section-heading">
            <div>
                <h2>Energy Map</h2>
                <p class="panel-subtitle">Understand how your devices contribute to total energy usage.</p>
            </div>
        </div>

        <div class="map-layout">

            <div class="panel">
                <h3>Consumption Distribution</h3>
                <p class="panel-subtitle">Daily energy consumption by device</p>

                <div class="donut-area">
                    <div class="donut" id="energyDonut">
                        <div class="donut-center">
                            <strong id="mapTotal">0</strong>
                            <small>kWh / day</small>
                        </div>
                    </div>
                </div>
            </div>

            <div class="panel">
                <h3>Device Breakdown</h3>
                <p class="panel-subtitle">Share of total daily energy consumption</p>
                <div id="mapBreakdown" class="energy-list"></div>
            </div>

        </div>

        <div class="panel" style="margin-top:20px;">
            <h3>How is this calculated?</h3>
            <p class="panel-subtitle" style="line-height:1.8;">
                Estimated daily energy = (Power in Watts × Operating Hours) ÷ 1000.
                The map updates when you add a device or change its information.
                These are estimates based on the values entered, not direct sensor measurements.
            </p>
        </div>

    </section>


    <!-- BUDGET PLANNER -->

    <section class="content-section" id="budget">

        <div class="section-heading">
            <div>
                <h2>Budget Planner</h2>
                <p class="panel-subtitle">Plan your electricity spending.</p>
            </div>
        </div>

        <div class="two-columns">

            <div class="panel">
                <h3>Budget Settings</h3>
                <p class="panel-subtitle">Set your monthly budget and electricity price.</p>

                <form onsubmit="saveBudget(event)">

                    <div class="field">
                        <label>Monthly Budget (EGP)</label>
                        <input type="number" id="budgetInput" min="1" required>
                    </div>

                    <div class="field">
                        <label>Electricity Price (EGP per kWh)</label>
                        <input type="number" id="priceInput" min="0" step="0.01" required>
                    </div>

                    <button class="small-btn" type="submit">Save Settings</button>

                </form>
            </div>

            <div class="panel">
                <h3>Monthly Estimate</h3>
                <p class="panel-subtitle">Based on your entered device information.</p>

                <p style="color:var(--muted);font-size:13px;margin-top:20px;">Estimated Monthly Cost</p>
                <div class="detail-value" id="budgetMonthlyCost">0 EGP</div>

                <p style="color:var(--muted);font-size:13px;margin-top:20px;">Remaining Budget</p>
                <div class="detail-value" id="budgetRemaining">0 EGP</div>

                <div class="progress-track">
                    <div class="progress-fill" id="budgetProgress" style="width:0%"></div>
                </div>

                <div class="budget-line">
                    <span id="budgetPercentage">0% used</span>
                    <span id="budgetTotalLabel">Budget: 0 EGP</span>
                </div>

            </div>

        </div>

    </section>


    <!-- ALERTS -->

    <section class="content-section" id="alerts">

        <div class="section-heading">
            <div>
                <h2>Alerts & Notifications</h2>
                <p class="panel-subtitle">Important updates about your energy usage.</p>
            </div>
        </div>

        <div id="alertsList"></div>

    </section>

</main>
</div>


<script>
/* BASIC AUTH SCREEN FUNCTIONS */

function showSignup() {
    document.getElementById("login").style.display = "none";
    document.getElementById("signup").style.display = "flex";
}

function showLogin() {
    document.getElementById("signup").style.display = "none";
    document.getElementById("login").style.display = "flex";
}

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

function toggleSidebar() {
    document.getElementById("sidebar").classList.toggle("open");
}

function showPage(page, element) {
    document.querySelectorAll(".content-section").forEach(section => {
        section.classList.remove("active");
    });

    const target = document.getElementById(page);

    if (target) {
        target.classList.add("active");
    }

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
        energyMap: ["Energy Map", "Explore your energy distribution"],
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

import { initializeApp } from
"https://www.gstatic.com/firebasejs/13.4.0/firebase-app.js";

import {
    getAuth,
    createUserWithEmailAndPassword,
    signInWithEmailAndPassword,
    sendPasswordResetEmail,
    updateProfile,
    GoogleAuthProvider,
    signInWithPopup,
    onAuthStateChanged,
    signOut
} from
"https://www.gstatic.com/firebasejs/13.4.0/firebase-auth.js";

import {
    getDatabase,
    ref,
    set,
    get
} from
"https://www.gstatic.com/firebasejs/13.4.0/firebase-database.js";


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
const database = getDatabase(app);

const googleProvider = new GoogleAuthProvider();
googleProvider.setCustomParameters({ prompt: "select_account" });


/* APP DATA */

let currentUser = null;
let appData = null;
let selectedDeviceId = null;

const defaultData = {
    settings: {
        monthlyBudget: 1000,
        pricePerKwh: 2.5
    },
    devices: {
        ac: {
            name: "Air Conditioner",
            type: "ac",
            watts: 1500,
            hours: 3,
            active: true
        },
        fridge: {
            name: "Refrigerator",
            type: "fridge",
            watts: 200,
            hours: 10,
            active: true
        },
        heater: {
            name: "Water Heater",
            type: "heater",
            watts: 2000,
            hours: 1,
            active: false
        },
        washing: {
            name: "Washing Machine",
            type: "washing",
            watts: 500,
            hours: 1,
            active: false
        }
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

const colors = [
    "#315d42",
    "#8dbd5d",
    "#b7c9a7",
    "#dce6d1",
    "#66866a",
    "#a4bd8b",
    "#c3d4b8"
];


/* HELPER FUNCTIONS */

function escapeHTML(value) {
    return String(value).replace(/[&<>"']/g, char => ({
        "&": "&amp;",
        "<": "&lt;",
        ">": "&gt;",
        '"': "&quot;",
        "'": "&#039;"
    })[char]);
}

function money(value) {
    return Number(value || 0).toLocaleString("en-US", {
        maximumFractionDigits: 2
    }) + " EGP";
}

function getDevices() {
    return Object.entries(appData.devices || {}).map(([id, device]) => ({
        id,
        ...device
    }));
}

function dailyKwh(device) {
    if (!device.active) return 0;
    return (Number(device.watts) * Number(device.hours)) / 1000;
}

function totalDailyKwh() {
    return getDevices().reduce((sum, device) => sum + dailyKwh(device), 0);
}

function monthlyKwh() {
    return totalDailyKwh() * 30;
}

function monthlyCost() {
    return monthlyKwh() * Number(appData.settings.pricePerKwh || 0);
}

function saveAppData() {
    if (!currentUser) return Promise.resolve();

    return set(
        ref(database, "users/" + currentUser.uid + "/energyWatch"),
        appData
    );
}

function showDashboard() {
    document.getElementById("authWrapper").style.display = "none";
    document.getElementById("dashboard").style.display = "block";
}

function showAuth() {
    document.getElementById("dashboard").style.display = "none";
    document.getElementById("authWrapper").style.display = "flex";
}


/* AUTHENTICATION */

window.signupUser = async function(event) {
    event.preventDefault();

    const button = document.getElementById("signupButton");

    const name = document.getElementById("signupName").value.trim();
    const email = document.getElementById("signupEmail").value.trim();
    const password = document.getElementById("signupPassword").value;
    const confirm = document.getElementById("confirmPassword").value;

    if (password !== confirm) {
        alert("Passwords do not match!");
        return;
    }

    button.disabled = true;
    button.textContent = "Creating account...";

    try {
        const result = await createUserWithEmailAndPassword(
            auth, email, password
        );

        await updateProfile(result.user, { displayName: name });

        alert("Your account has been created successfully!");

    } catch (error) {
        console.error(error);
        alert("Sign Up Error: " + error.message);
    } finally {
        button.disabled = false;
        button.textContent = "Sign Up →";
    }
};


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

        if (error.code === "auth/invalid-credential") {
            alert("Incorrect email or password.");
        } else {
            alert("Login Error: " + error.message);
        }
    } finally {
        button.disabled = false;
        button.textContent = "Log In →";
    }
};


window.googleLogin = async function() {
    try {
        await signInWithPopup(auth, googleProvider);
    } catch (error) {
        console.error(error);

        if (error.code === "auth/popup-closed-by-user") {
            alert("Google sign-in was cancelled.");
        } else {
            alert("Google Login Error: " + error.message);
        }
    }
};


window.forgotPassword = async function() {
    const email = document.getElementById("loginEmail").value.trim();

    if (!email) {
        alert("Please enter your email address first.");
        return;
    }

    try {
        await sendPasswordResetEmail(auth, email);
        alert("Password reset email sent successfully!");
    } catch (error) {
        alert("Password Reset Error: " + error.message);
    }
};


window.logoutUser = async function() {
    try {
        await signOut(auth);
        appData = null;
        currentUser = null;
        showAuth();
        showLogin();
    } catch (error) {
        alert("Logout Error: " + error.message);
    }
};


/* AUTH STATE AND DATABASE LOADING */

onAuthStateChanged(auth, async (user) => {
    if (!user) {
        currentUser = null;
        appData = null;
        showAuth();
        return;
    }

    currentUser = user;

    try {
        const userRef = ref(
            database,
            "users/" + user.uid + "/energyWatch"
        );

        const snapshot = await get(userRef);

        if (snapshot.exists()) {
            appData = snapshot.val();

            if (!appData.settings) {
                appData.settings = {...defaultData.settings};
            }

            if (!appData.devices) {
                appData.devices = {};
            }

        } else {
            appData = JSON.parse(JSON.stringify(defaultData));
            await saveAppData();
        }

        showDashboard();
        updateUserInfo();
        renderEverything();

    } catch (error) {
        console.error("Database Error:", error);
        alert("Could not load your data. Check your Firebase Database rules and internet connection.");
    }
});


function updateUserInfo() {
    const name = currentUser.displayName || "Energy Watch User";
    const email = currentUser.email || "";

    document.getElementById("userName").textContent = name;
    document.getElementById("userEmail").textContent = email;
    document.getElementById("userAvatar").textContent =
        name.charAt(0).toUpperCase();

    document.getElementById("welcomeMessage").textContent =
        "Welcome, " + name + "!";
}


/* RENDER FUNCTIONS */

function renderEverything() {
    if (!appData) return;

    renderHome();
    renderDevices();
    renderEnergyMap();
    renderBudget();
    renderAlerts();
}


function renderHome() {
    const devices = getDevices();
    const total = totalDailyKwh();
    const cost = monthlyCost();

    document.getElementById("dailyUsage").textContent =
        total.toFixed(2) + " kWh";

    document.getElementById("monthlyCost").textContent =
        money(cost);

    document.getElementById("deviceCount").textContent =
        devices.length;

    document.getElementById("activeCount").textContent =
        devices.filter(device => device.active).length;

    const budget = Number(appData.settings.monthlyBudget || 0);
    const percentage = budget > 0 ? (cost / budget) * 100 : 0;

    document.getElementById("homeBudgetCost").textContent =
        money(cost);

    document.getElementById("homeBudgetUsed").textContent =
        "Used: " + money(cost);

    document.getElementById("homeBudgetLimit").textContent =
        "Limit: " + money(budget);

    document.getElementById("homeBudgetProgress").style.width =
        Math.min(percentage, 100) + "%";

    const list = document.getElementById("homeEnergyList");

    const sorted = [...devices].sort(
        (a, b) => dailyKwh(b) - dailyKwh(a)
    );

    if (sorted.length === 0) {
        list.innerHTML = '<div class="empty-state">No devices added yet.</div>';
    } else {
        const max = Math.max(...sorted.map(d => dailyKwh(d)), 0.01);

        list.innerHTML = sorted.slice(0, 5).map(device => `
            <div class="energy-item">
                <span class="energy-emoji">${icons[device.type] || "🔌"}</span>
                <div>
                    <strong>${escapeHTML(device.name)}</strong>
                    <div class="progress-track">
                        <div class="progress-fill"
                        style="width:${(dailyKwh(device)/max)*100}%"></div>
                    </div>
                </div>
                <strong>${dailyKwh(device).toFixed(2)} kWh</strong>
            </div>
        `).join("");
    }

    document.getElementById("homeDeviceGrid").innerHTML =
        devices.slice(0, 3).map(deviceCardHTML).join("") ||
        '<div class="empty-state">Add your first device from the Devices page.</div>';
}


function deviceCardHTML(device) {
    const usage = dailyKwh(device);

    return `
        <div class="device-card">
            <div class="device-top">
                <div class="device-emoji">${icons[device.type] || "🔌"}</div>
                <span class="status ${device.active ? "" : "off"}">
                    ${device.active ? "Active" : "Inactive"}
                </span>
            </div>

            <h3>${escapeHTML(device.name)}</h3>
            <p>${Number(device.watts)} Watts • ${Number(device.hours)} hours/day</p>

            <div class="device-metrics">
                <span>Daily usage</span>
                <strong>${usage.toFixed(2)} kWh</strong>
            </div>

            <div class="device-actions">
                <button onclick="openDeviceDetails('${escapeHTML(device.id)}')">Details</button>
                <button onclick="toggleDevice('${escapeHTML(device.id)}')">
                    ${device.active ? "Turn Off" : "Turn On"}
                </button>
            </div>
        </div>
    `;
}


function renderDevices() {
    const devices = getDevices();

    document.getElementById("allDeviceGrid").innerHTML =
        devices.map(deviceCardHTML).join("") ||
        '<div class="empty-state"><span>🔌</span>No devices yet. Add your first device above.</div>';
}


function renderEnergyMap() {
    const devices = getDevices();
    const total = totalDailyKwh();

    document.getElementById("mapTotal").textContent =
        total.toFixed(2);

    const activeDevices = devices.filter(d => dailyKwh(d) > 0);

    if (total <= 0 || activeDevices.length === 0) {
        document.getElementById("energyDonut").style.background = "#e9eee0";
        document.getElementById("mapBreakdown").innerHTML =
            '<div class="empty-state">Turn on a device and enter its operating hours to see your Energy Map.</div>';
        return;
    }

    let currentAngle = 0;
    const segments = [];

    activeDevices.forEach((device, index) => {
        const share = dailyKwh(device) / total;
        const nextAngle = currentAngle + share * 360;

        segments.push(
            `${colors[index % colors.length]} ${currentAngle}deg ${nextAngle}deg`
        );

        currentAngle = nextAngle;
    });

    document.getElementById("energyDonut").style.background =
        `conic-gradient(${segments.join(",")})`;

    document.getElementById("mapBreakdown").innerHTML =
        activeDevices.map((device, index) => {
            const share = (dailyKwh(device) / total) * 100;

            return `
                <div class="energy-item">
                    <span class="energy-emoji">${icons[device.type] || "🔌"}</span>
                    <div>
                        <strong>${escapeHTML(device.name)}</strong>
                        <div class="progress-track">
                            <div class="progress-fill"
                            style="width:${share}%;background:${colors[index % colors.length]}"></div>
                        </div>
                        <small>${share.toFixed(1)}% of daily consumption</small>
                    </div>
                    <strong>${dailyKwh(device).toFixed(2)} kWh</strong>
                </div>
            `;
        }).join("");
}


function renderBudget() {
    const budget = Number(appData.settings.monthlyBudget || 0);
    const price = Number(appData.settings.pricePerKwh || 0);
    const cost = monthlyCost();

    const remaining = budget - cost;
    const percentage = budget > 0 ? (cost / budget) * 100 : 0;

    document.getElementById("budgetInput").value = budget;
    document.getElementById("priceInput").value = price;

    document.getElementById("budgetMonthlyCost").textContent =
        money(cost);

    document.getElementById("budgetRemaining").textContent =
        money(remaining);

    document.getElementById("budgetProgress").style.width =
        Math.min(percentage, 100) + "%";

    document.getElementById("budgetPercentage").textContent =
        percentage.toFixed(1) + "% used";

    document.getElementById("budgetTotalLabel").textContent =
        "Budget: " + money(budget);
}


function renderAlerts() {
    const alerts = [];

    const budget = Number(appData.settings.monthlyBudget || 0);
    const cost = monthlyCost();

    if (budget > 0 && cost > budget) {
        alerts.push({
            icon: "⚠️",
            title: "Monthly Budget Exceeded",
            text: "Your estimated monthly electricity cost is higher than your budget."
        });
    } else if (budget > 0 && cost >= budget * 0.8) {
        alerts.push({
            icon: "💡",
            title: "Budget Almost Reached",
            text: "Your estimated monthly cost has reached 80% of your budget."
        });
    }

    const devices = getDevices();

    devices.forEach(device => {
        if (device.active && Number(device.hours) >= 8) {
            alerts.push({
                icon: "⏱️",
                title: device.name + " Usage Notice",
                text: "This device has a daily operating time of 8 hours or more. Review whether this matches your normal usage."
            });
        }
    });

    if (alerts.length === 0) {
        document.getElementById("alertsList").innerHTML = `
            <div class="panel empty-state">
                <span>🌿</span>
                <h3>Everything looks good!</h3>
                <p>No alerts at the moment. Keep monitoring your energy usage.</p>
            </div>
        `;
        return;
    }

    document.getElementById("alertsList").innerHTML =
        alerts.map(alert => `
            <div class="alert-card">
                <div class="alert-icon">${alert.icon}</div>
                <div>
                    <strong>${escapeHTML(alert.title)}</strong>
                    <p>${escapeHTML(alert.text)}</p>
                </div>
            </div>
        `).join("");
}


/* DEVICE ACTIONS */

window.addDevice = async function(event) {
    event.preventDefault();

    const name = document.getElementById("newDeviceName").value.trim();
    const type = document.getElementById("newDeviceType").value;
    const watts = Number(document.getElementById("newDeviceWatts").value);
    const hours = Number(document.getElementById("newDeviceHours").value);

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
        event.target.reset();
        renderEverything();
        alert("Device added successfully!");
    } catch (error) {
        console.error(error);
        alert("Could not save this device. Please try again.");
    }
};


window.toggleDevice = async function(id) {
    const device = appData.devices[id];
    if (!device) return;

    device.active = !device.active;

    try {
        await saveAppData();
        renderEverything();
    } catch (error) {
        console.error(error);
        alert("Could not update device status.");
    }
};


window.openDeviceDetails = function(id) {
    const device = appData.devices[id];
    if (!device) return;

    selectedDeviceId = id;

    document.getElementById("detailName").textContent = device.name;

    document.getElementById("editDeviceName").value = device.name;
    document.getElementById("editDeviceWatts").value = device.watts;
    document.getElementById("editDeviceHours").value = device.hours;
    document.getElementById("editDeviceStatus").value =
        String(device.active);

    const daily = dailyKwh(device);
    const monthly = daily * 30;
    const cost = monthly * Number(appData.settings.pricePerKwh || 0);

    document.getElementById("detailDaily").textContent =
        daily.toFixed(2) + " kWh";

    document.getElementById("detailMonthly").textContent =
        monthly.toFixed(2) + " kWh";

    document.getElementById("detailCost").textContent =
        money(cost);

    showPageById("details");
};


window.saveDeviceDetails = async function(event) {
    event.preventDefault();

    if (!selectedDeviceId || !appData.devices[selectedDeviceId]) return;

    const name = document.getElementById("editDeviceName").value.trim();
    const watts = Number(document.getElementById("editDeviceWatts").value);
    const hours = Number(document.getElementById("editDeviceHours").value);
    const active =
        document.getElementById("editDeviceStatus").value === "true";

    if (!name || watts <= 0 || hours < 0 || hours > 24) {
        alert("Please enter valid information.");
        return;
    }

    const device = appData.devices[selectedDeviceId];

    device.name = name;
    device.watts = watts;
    device.hours = hours;
    device.active = active;

    try {
        await saveAppData();
        renderEverything();
        openDeviceDetails(selectedDeviceId);
        alert("Device information updated!");
    } catch (error) {
        console.error(error);
        alert("Could not save changes.");
    }
};


/* BUDGET ACTION */

window.saveBudget = async function(event) {
    event.preventDefault();

    const budget = Number(document.getElementById("budgetInput").value);
    const price = Number(document.getElementById("priceInput").value);

    if (budget <= 0 || price < 0) {
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

</script>

</body>
</html>
