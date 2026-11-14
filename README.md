
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Energy Watch</title>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700;800&display=swap');

:root {
    --dark: #193f2e;
    --green: #285b3c;
    --light-green: #83aa57;
    --cream: #fbfaf5;
    --border: #deded5;
}

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Poppins', sans-serif;
}

body {
    min-height: 100vh;
    background: #e9ebe5;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 20px;
}

.app {
    width: 100%;
    max-width: 430px;
    min-height: 850px;
    position: relative;
    background: var(--cream);
    border: 1px solid #deded9;
    border-radius: 35px;
    overflow: hidden;
    box-shadow: 0 15px 45px #193f2e18;
}

.screen {
    width: 100%;
    min-height: 850px;
    display: none;
    position: relative;
    overflow: hidden;
    background: var(--cream);
    animation: appear .4s ease;
}

.screen.active {
    display: flex;
    flex-direction: column;
}

@keyframes appear {
    from {
        opacity: 0;
        transform: translateY(8px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

/* TOP DECORATION */

.top-decoration {
    position: absolute;
    width: 350px;
    height: 230px;
    top: -145px;
    right: -90px;
    background: #e9eee0;
    border-radius: 50%;
    z-index: 0;
}

.leaf-decoration {
    position: absolute;
    width: 100px;
    height: 120px;
    z-index: 2;
    pointer-events: none;
}

.leaf-decoration svg {
    width: 100%;
    height: 100%;
}

/* STATUS BAR */

.status {
    display: flex;
    justify-content: space-between;
    padding: 22px 27px 0;
    font-size: 14px;
    font-weight: 700;
    color: #111;
    position: relative;
    z-index: 3;
}

.status-icons {
    letter-spacing: 3px;
}

/* WELCOME */

.welcome {
    align-items: center;
}

.welcome-leaves {
    top: 20px;
    left: -12px;
    width: 125px;
    height: 190px;
}

.welcome-content {
    width: 100%;
    text-align: center;
    position: relative;
    z-index: 2;
    padding-top: 90px;
}

.logo {
    width: 155px;
    height: 140px;
    margin: 0 auto 0;
}

.logo svg {
    width: 100%;
    height: 100%;
}

.brand-name {
    font-size: 43px;
    font-weight: 700;
    letter-spacing: -2px;
    color: var(--dark);
    line-height: 1.3;
}

.brand-name span {
    color: var(--light-green);
}

.tagline {
    font-size: 17px;
    font-weight: 500;
    margin-top: 9px;
    color: #1c3024;
}

.house-scene {
    width: 100%;
    height: 270px;
    margin-top: 25px;
    display: block;
}

.welcome-description {
    font-size: 15px;
    color: #555e53;
    margin: 5px 30px 25px;
    line-height: 1.7;
}

.main-btn {
    width: 85%;
    height: 59px;
    border: none;
    border-radius: 35px;
    background: linear-gradient(110deg, #183f2c, #326143);
    color: white;
    font-size: 18px;
    font-weight: 600;
    cursor: pointer;
    transition: .3s;
    box-shadow: 0 5px 15px #193f2e20;
}

.main-btn:hover {
    transform: translateY(-3px);
    box-shadow: 0 9px 20px #193f2e30;
}

.main-btn span {
    font-size: 23px;
    margin-left: 10px;
}

.welcome-footer {
    margin-top: 20px;
    font-size: 12px;
    color: #8b9588;
    letter-spacing: 1px;
}

/* LOGIN */

.login {
    padding-bottom: 30px;
}

.login-leaf {
    top: 5px;
    right: -10px;
    width: 100px;
    height: 120px;
}

.login-brand {
    text-align: center;
    margin-top: 25px;
    position: relative;
    z-index: 2;
}

.login-brand .logo {
    width: 115px;
    height: 105px;
}

.login-brand .brand-name {
    font-size: 38px;
}

.login-brand .tagline {
    font-size: 15px;
    margin-top: 5px;
}

.city-scene {
    width: 100%;
    height: 150px;
    margin-top: 10px;
    display: block;
}

.form-area {
    width: 100%;
    padding: 0 36px;
    position: relative;
    z-index: 2;
}

.form-heading {
    font-size: 27px;
    font-weight: 700;
    color: var(--dark);
    margin-bottom: 2px;
}

.form-subtitle {
    font-size: 13px;
    color: #73756f;
    margin-bottom: 20px;
}

.input-box {
    width: 100%;
    height: 55px;
    border: 1px solid var(--border);
    border-radius: 17px;
    display: flex;
    align-items: center;
    padding: 0 14px;
    gap: 13px;
    background: #f8f7f1;
    margin-bottom: 12px;
    transition: .3s;
}

.input-box:focus-within {
    border-color: #62866a;
    box-shadow: 0 0 0 3px #285b3c12;
}

.input-icon {
    font-size: 19px;
    color: var(--dark);
    width: 22px;
    text-align: center;
}

.input-box input {
    flex: 1;
    width: 0;
    border: none;
    outline: none;
    background: transparent;
    font-size: 14px;
    color: var(--dark);
}

.input-box input::placeholder {
    color: #777a76;
}

.eye {
    background: none;
    border: none;
    color: #777;
    cursor: pointer;
    font-size: 19px;
}

.forgot {
    text-align: right;
    margin: 7px 0 18px;
}

.forgot a {
    font-size: 12px;
    color: var(--dark);
    font-weight: 500;
    cursor: pointer;
}

.form-area .main-btn {
    width: 100%;
    height: 56px;
    font-size: 17px;
}

.divider {
    display: flex;
    align-items: center;
    gap: 12px;
    color: #666;
    font-size: 13px;
    margin: 15px 0;
}

.divider::before,
.divider::after {
    content: "";
    height: 1px;
    background: #d5d5ce;
    flex: 1;
}

.google-btn {
    width: 100%;
    height: 51px;
    border: 1px solid #263a2e;
    background: transparent;
    border-radius: 28px;
    font-size: 14px;
    color: #171717;
    cursor: pointer;
    transition: .3s;
}

.google-btn:hover {
    background: #eff2e9;
}

.google-letter {
    font-size: 21px;
    font-weight: 700;
    margin-right: 8px;
    background: conic-gradient(#4285f4 0 25%,#34a853 25% 50%,#fbbc05 50% 75%,#ea4335 75%);
    background-clip: text;
    -webkit-text-fill-color: transparent;
}

.switch-text {
    text-align: center;
    margin-top: 20px;
    font-size: 12px;
    color: #202020;
}

.switch-text a {
    color: var(--dark);
    font-weight: 700;
    margin-left: 5px;
    cursor: pointer;
}

.corner-leaf {
    position: absolute;
    width: 100px;
    height: 90px;
    bottom: -25px;
    right: -15px;
    background: #e5eddd;
    border-radius: 100% 0 0 0;
    z-index: 0;
}

/* SIGN UP */

.signup {
    padding-bottom: 125px;
}

.signup-leaf {
    top: 5px;
    right: -10px;
    width: 95px;
    height: 120px;
}

.back-btn {
    position: relative;
    z-index: 3;
    margin: 38px 0 30px 30px;
    width: 49px;
    height: 49px;
    background: #fff;
    border: 1px solid #e1e1db;
    border-radius: 50%;
    color: var(--dark);
    font-size: 24px;
    cursor: pointer;
    box-shadow: 0 3px 10px #0000000a;
    transition: .3s;
}

.back-btn:hover {
    transform: translateX(-3px);
}

.signup-heading {
    text-align: center;
    padding: 0 15px;
    position: relative;
    z-index: 2;
}

.signup-heading h2 {
    font-size: 29px;
    color: var(--dark);
    margin-bottom: 9px;
    font-weight: 700;
}

.signup-heading p {
    font-size: 15px;
    line-height: 1.6;
    color: #30332f;
}

.signup .form-area {
    margin-top: 28px;
}

.signup .input-box {
    height: 57px;
    margin-bottom: 13px;
}

.signup .main-btn {
    margin-top: 10px;
}

.signup .divider {
    margin-top: 17px;
}

.signup .switch-text {
    margin-top: 25px;
}

/* SIGNUP BOTTOM LANDSCAPE */

.bottom-scene {
    position: absolute;
    bottom: 0;
    left: 0;
    width: 100%;
    height: 120px;
    z-index: 0;
    pointer-events: none;
}

/* RESPONSIVE */

@media(max-width:480px) {
    body {
        padding: 0;
        background: var(--cream);
    }

    .app {
        max-width: 100%;
        min-height: 100vh;
        border: none;
        border-radius: 0;
        box-shadow: none;
    }

    .screen {
        min-height: 100vh;
    }

    .welcome-content {
        padding-top: 75px;
    }
}

@media(max-height:800px) and (min-width:481px) {
    .screen {
        min-height: 800px;
    }

    .welcome-content {
        padding-top: 50px;
    }

    .house-scene {
        height: 230px;
    }
}
</style>
</head>

<body>

<main class="app">

<!-- ================= WELCOME SCREEN ================= -->

<section class="screen welcome active" id="welcome">

    <div class="top-decoration"></div>

    <div class="leaf-decoration welcome-leaves">
        <svg viewBox="0 0 120 180">
            <path d="M20 170 Q25 90 85 20"
                  fill="none" stroke="#4e8050" stroke-width="3"/>
            <path d="M35 115 C0 90 5 45 8 30 C55 43 63 83 35 115Z"
                  fill="#9abd7c"/>
            <path d="M50 90 C55 35 90 15 112 10 C113 65 83 91 50 90Z"
                  fill="#477d4c"/>
            <path d="M20 140 C5 110 20 88 42 80 C52 112 42 135 20 140Z"
                  fill="#a9c995"/>
        </svg>
    </div>

    <div class="status">
        <span>9:41</span>
        <span class="status-icons">▮▮ ◉ ▰</span>
    </div>

    <div class="welcome-content">

        <div class="logo">
            <svg viewBox="0 0 180 160">
                <path d="M25 70 L90 12 L155 70"
                      fill="none" stroke="#173f2d"
                      stroke-width="9" stroke-linecap="round"
                      stroke-linejoin="round"/>
                <path d="M40 65 V140 Q40 145 48 145 H135 Q140 145 140 137 V65"
                      fill="none" stroke="#173f2d" stroke-width="9"/>
                <path d="M87 55 L65 95 H88 L77 127 L115 80 H94 L105 55Z"
                      fill="#80aa48"/>
                <path d="M115 105 C120 55 150 32 174 30 C174 78 151 112 115 128Z"
                      fill="#79a64d"/>
                <path d="M115 128 Q140 80 159 51"
                      fill="none" stroke="#f7f7ed" stroke-width="3"/>
            </svg>
        </div>

        <h1 class="brand-name">Energy <span>Watch</span></h1>

        <p class="tagline">Monitor • Save • Live Green</p>

        <!-- HOUSE AND SOLAR PANELS -->

        <svg class="house-scene" viewBox="0 0 430 290">

            <defs>
                <linearGradient id="houseSky" x1="0" y1="0" x2="0" y2="1">
                    <stop offset="0" stop-color="#f7f8f0"/>
                    <stop offset="1" stop-color="#dce8d5"/>
                </linearGradient>
            </defs>

            <rect width="430" height="290" fill="url(#houseSky)"/>

            <!-- Sun -->
            <circle cx="350" cy="45" r="27" fill="#e8eddb"/>

            <!-- House shadow -->
            <ellipse cx="230" cy="258" rx="160" ry="15" fill="#c6d8bd"/>

            <!-- House -->
            <path d="M105 132 L215 42 L335 132"
                  fill="#f5f4e9" stroke="#3b6743"
                  stroke-width="6" stroke-linejoin="round"/>

            <rect x="126" y="128" width="185" height="125"
                  fill="#f9f7ee" stroke="#3b6743" stroke-width="5"/>

            <!-- Roof -->
            <path d="M155 104 L280 110 L270 148 L143 141Z"
                  fill="#426d78" stroke="#315a3d" stroke-width="4"/>

            <path d="M180 105 L170 143 M210 107 L200 145 M240 109 L230 147 M155 123 L275 129"
                  stroke="#d4e3e0" stroke-width="2"/>

            <!-- Windows -->
            <rect x="145" y="160" width="50" height="45"
                  fill="#b5d2c2" stroke="#426d4a" stroke-width="4"/>
            <path d="M170 160 V205 M145 183 H195"
                  stroke="#426d4a" stroke-width="3"/>

            <rect x="242" y="160" width="50" height="45"
                  fill="#b5d2c2" stroke="#426d4a" stroke-width="4"/>
            <path d="M267 160 V205 M242 183 H292"
                  stroke="#426d4a" stroke-width="3"/>

            <!-- Door -->
            <rect x="202" y="195" width="33" height="58"
                  fill="#a5c19b" stroke="#426d4a" stroke-width="4"/>
            <circle cx="228" cy="226" r="2" fill="#315a3d"/>

            <!-- Left tree -->
            <path d="M62 258 V151" stroke="#456a43" stroke-width="8"/>
            <circle cx="62" cy="135" r="35" fill="#75a263"/>
            <circle cx="35" cy="155" r="25" fill="#8ab477"/>
            <circle cx="87" cy="157" r="25" fill="#649453"/>
            <circle cx="58" cy="110" r="23" fill="#8ab477"/>

            <!-- Right tree -->
            <path d="M360 260 V174" stroke="#456a43" stroke-width="8"/>
            <circle cx="360" cy="158" r="31" fill="#6b9859"/>
            <circle cx="338" cy="174" r="22" fill="#8ab477"/>
            <circle cx="383" cy="178" r="22" fill="#75a263"/>

            <!-- Bushes -->
            <g fill="#759c62">
                <circle cx="15" cy="248" r="22"/>
                <circle cx="37" cy="252" r="20"/>
                <circle cx="393" cy="249" r="24"/>
                <circle cx="415" cy="253" r="19"/>
            </g>

            <!-- Grass -->
            <path d="M0 255 Q100 230 210 260 T430 245 V290 H0Z"
                  fill="#9cbd86"/>

        </svg>

        <p class="welcome-description">
            Save energy today for a greener tomorrow.
        </p>

        <button class="main-btn" onclick="showScreen('login')">
            Get Started <span>→</span>
        </button>

        <p class="welcome-footer">SMART ENERGY MANAGEMENT</p>

    </div>

    <div class="corner-leaf"></div>

</section>


<!-- ================= LOGIN SCREEN ================= -->

<section class="screen login" id="login">

    <div class="top-decoration"></div>

    <div class="leaf-decoration login-leaf">
        <svg viewBox="0 0 120 140">
            <path d="M5 130 Q55 65 100 10"
                  fill="none" stroke="#4c8050" stroke-width="3"/>
            <path d="M50 75 C25 40 45 15 60 5 C88 40 80 65 50 75Z"
                  fill="#477c4d"/>
        </svg>
    </div>

    <div class="status">
        <span>9:41</span>
        <span class="status-icons">▮▮ ◉ ▰</span>
    </div>

    <div class="login-brand">

        <div class="logo">
            <svg viewBox="0 0 180 160">
                <path d="M25 70 L90 12 L155 70"
                      fill="none" stroke="#173f2d"
                      stroke-width="9" stroke-linecap="round"/>
                <path d="M40 65 V140 H140 V65"
                      fill="none" stroke="#173f2d" stroke-width="9"/>
                <path d="M87 55 L65 95 H88 L77 127 L115 80 H94 L105 55Z"
                      fill="#80aa48"/>
                <path d="M115 105 C120 55 150 32 174 30 C174 78 151 112 115 128Z"
                      fill="#79a64d"/>
                <path d="M115 128 Q140 80 159 51"
                      fill="none" stroke="#f7f7ed" stroke-width="3"/>
            </svg>
        </div>

        <h1 class="brand-name">Energy <span>Watch</span></h1>
        <p class="tagline">Monitor • Save • Live Green</p>

    </div>

    <!-- CITY ILLUSTRATION -->

    <svg class="city-scene" viewBox="0 0 500 160">

        <rect width="500" height="160" fill="#f0f2e8"/>

        <g fill="#b9cbb4">
            <path d="M20 140V70H48V140Z"/>
            <path d="M65 140V40H100V140Z"/>
            <path d="M110 140V85H140V140Z"/>
            <path d="M150 140V30H183V140Z"/>
            <path d="M195 140V65H226V140Z"/>
            <path d="M240 140V40H275V140Z"/>
            <path d="M285 140V72H315V140Z"/>
            <path d="M325 140V20H360V140Z"/>
            <path d="M375 140V55H405V140Z"/>
            <path d="M420 140V40H455V140Z"/>
            <path d="M465 140V80H490V140Z"/>
        </g>

        <path d="M0 137 Q90 100 160 132 T300 130 T500 125 V160 H0Z"
              fill="#9bb994"/>

        <!-- Trees -->
        <g fill="#689354">
            <circle cx="55" cy="113" r="22"/>
            <circle cx="34" cy="130" r="19"/>
            <circle cx="76" cy="132" r="18"/>
            <circle cx="430" cy="117" r="25"/>
            <circle cx="405" cy="134" r="20"/>
            <circle cx="455" cy="135" r="18"/>
        </g>

        <g stroke="#426b43" stroke-width="5">
            <path d="M55 125V158"/>
            <path d="M430 130V158"/>
        </g>

        <path d="M0 150 Q100 123 230 151 T500 143 V160 H0Z"
              fill="#709966"/>

    </svg>

    <div class="form-area">

        <h2 class="form-heading">Welcome back</h2>

        <p class="form-subtitle">
            Log in to your Energy Watch account
        </p>

        <form id="loginForm">

            <div class="input-box">
                <span class="input-icon">✉</span>
                <input type="email" placeholder="Email Address" required>
            </div>

            <div class="input-box">
                <span class="input-icon">♙</span>
                <input type="password"
                       id="loginPassword"
                       placeholder="Password"
                       required>
                <button type="button" class="eye"
                        onclick="togglePassword('loginPassword',this)">
                    ◉
                </button>
            </div>

            <div class="forgot">
                <a onclick="forgotPassword()">Forgot Password?</a>
            </div>

            <button type="submit" class="main-btn">
                Log In <span>→</span>
            </button>

        </form>

        <div class="divider">OR</div>

        <button class="google-btn" onclick="googleLogin()">
            <span class="google-letter">G</span>
            Continue with Google
        </button>

        <p class="switch-text">
            Don't have an account?
            <a onclick="showScreen('signup')">Sign Up</a>
        </p>

    </div>

    <div class="corner-leaf"></div>

</section>


<!-- ================= SIGN UP SCREEN ================= -->

<section class="screen signup" id="signup">

    <div class="top-decoration"></div>

    <div class="leaf-decoration signup-leaf">
        <svg viewBox="0 0 120 140">
            <path d="M10 120 Q65 70 110 10"
                  fill="none" stroke="#4c8050" stroke-width="3"/>
            <path d="M55 80 C28 43 47 15 65 5 C95 42 82 72 55 80Z"
                  fill="#477c4d"/>
        </svg>
    </div>

    <div class="status">
        <span>9:41</span>
        <span class="status-icons">▮▮ ◉ ▰</span>
    </div>

    <button class="back-btn" onclick="showScreen('login')">
        ←
    </button>

    <div class="signup-heading">

        <h2>Create Your Account</h2>

        <p>
            Join Energy Watch and start<br>
            managing your energy smarter!
        </p>

    </div>

    <div class="form-area">

        <form id="signupForm">

            <div class="input-box">
                <span class="input-icon">♟</span>
                <input type="text"
                       placeholder="Full Name"
                       required>
            </div>

            <div class="input-box">
                <span class="input-icon">✉</span>
                <input type="email"
                       placeholder="Email Address"
                       required>
            </div>

            <div class="input-box">
                <span class="input-icon">♙</span>
                <input type="password"
                       id="signupPassword"
                       placeholder="Password"
                       minlength="6"
                       required>
                <button type="button" class="eye"
                        onclick="togglePassword('signupPassword',this)">
                    ◉
                </button>
            </div>

            <div class="input-box">
                <span class="input-icon">♙</span>
                <input type="password"
                       id="confirmPassword"
                       placeholder="Confirm Password"
                       minlength="6"
                       required>
                <button type="button" class="eye"
                        onclick="togglePassword('confirmPassword',this)">
                    ◉
                </button>
            </div>

            <button type="submit" class="main-btn">
                Create Account <span>→</span>
            </button>

        </form>

        <div class="divider">OR</div>

        <button class="google-btn" onclick="googleLogin()">
            <span class="google-letter">G</span>
            Continue with Google
        </button>

        <p class="switch-text">
            Already have an account?
            <a onclick="showScreen('login')">Log In</a>
        </p>

    </div>

    <!-- BOTTOM GREEN ENERGY LANDSCAPE -->

    <svg class="bottom-scene" viewBox="0 0 500 120"
         preserveAspectRatio="none">

        <path d="M0 65 Q90 35 180 72 T350 62 T500 55 V120 H0Z"
              fill="#e5eddd"/>

        <path d="M0 88 Q100 55 220 91 T500 72 V120 H0Z"
              fill="#b8d0a8"/>

        <!-- Wind turbine 1 -->
        <g stroke="#3d6549" stroke-width="3" fill="none">
            <path d="M70 110V42"/>
            <path d="M70 42L52 27"/>
            <path d="M70 42L88 26"/>
            <path d="M70 42L68 62"/>
        </g>

        <!-- Wind turbine 2 -->
        <g stroke="#3d6549" stroke-width="2.5" fill="none">
            <path d="M125 112V65"/>
            <path d="M125 65L111 52"/>
            <path d="M125 65L139 52"/>
            <path d="M125 65L124 81"/>
        </g>

        <!-- Solar panels -->
        <path d="M330 105L380 85L432 103L382 117Z"
              fill="#315b70" stroke="#f5f6ed" stroke-width="2"/>

        <path d="M355 95L353 110 M380 87L380 115 M405 95L407 110"
              stroke="#dce8e5" stroke-width="2"/>

        <g fill="#719b60">
            <circle cx="470" cy="85" r="25"/>
            <circle cx="448" cy="100" r="20"/>
        </g>

    </svg>

</section>

</main>


<!-- ================= JAVASCRIPT ================= -->

<script>

// SWITCH BETWEEN SCREENS

function showScreen(screenId) {

    document.querySelectorAll('.screen').forEach(screen => {
        screen.classList.remove('active');
    });

    document.getElementById(screenId).classList.add('active');

    window.scrollTo(0, 0);
}


// SHOW AND HIDE PASSWORD

function togglePassword(id, button) {

    const input = document.getElementById(id);

    if (input.type === "password") {
        input.type = "text";
        button.textContent = "◎";
    } else {
        input.type = "password";
        button.textContent = "◉";
    }
}


// LOGIN FORM

document.getElementById('loginForm').addEventListener('submit', function(event) {

    event.preventDefault();

    alert("Welcome to Energy Watch!");

});


// SIGN UP FORM

document.getElementById('signupForm').addEventListener('submit', function(event) {

    event.preventDefault();

    const password = document.getElementById('signupPassword').value;

    const confirm = document.getElementById('confirmPassword').value;

    if (password !== confirm) {

        alert("Passwords do not match!");

        return;
    }

    alert("Your account has been created successfully!");

    showScreen('login');

});


// FORGOT PASSWORD

function forgotPassword() {

    alert("Password recovery will be available soon!");

}


// GOOGLE LOGIN

function googleLogin() {

    alert("Google authentication needs to be connected.");

}

</script>

</body>
</html>
