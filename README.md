
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Energy Watch</title>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: Arial, sans-serif;
}

body {
    min-height: 100vh;
    background: #f7f7f2;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 30px;
    color: #183d2d;
}

.container {
    width: 100%;
    max-width: 1050px;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 65px;
    align-items: center;
}

.phone {
    min-height: 850px;
    background: #fbfaf6;
    border: 2px solid #deded8;
    border-radius: 48px;
    overflow: hidden;
    position: relative;
    box-shadow: 0 10px 25px #00000012;
    padding: 30px 45px;
    display: flex;
    flex-direction: column;
    align-items: center;
}

.phone::before {
    content: "";
    position: absolute;
    width: 350px;
    height: 250px;
    background: #e9eee0;
    border-radius: 0 0 100% 100%;
    top: -150px;
    right: -50px;
    opacity: .8;
}

.phone > * {
    position: relative;
    z-index: 1;
}

.logo {
    text-align: center;
    margin-top: 100px;
}

.logo-icon {
    font-size: 100px;
    color: #1c4a34;
    line-height: 1.2;
}

.logo h1 {
    font-size: 43px;
    font-weight: 750;
    letter-spacing: -2px;
    margin-top: 12px;
}

.logo h1 span {
    color: #74a943;
}

.tagline {
    font-size: 19px;
    margin-top: 13px;
    color: #172d23;
}

.city {
    height: 140px;
    width: calc(100% + 90px);
    margin-top: 25px;
    position: relative;
    background: linear-gradient(to top, #a8c69c, #edf2e7);
    clip-path: polygon(0 65%, 12% 50%, 22% 65%, 35% 38%, 50% 60%, 63% 35%, 77% 60%, 90% 30%, 100% 55%, 100% 100%, 0 100%);
}

.city::before {
    content: "▥  ▥  ▥  ▥  ▥  ▥  ▥";
    position: absolute;
    font-size: 65px;
    color: #a2bba2;
    bottom: 0;
    left: 10px;
    letter-spacing: -5px;
}

.form {
    width: 100%;
    margin-top: 20px;
}

.input-box {
    width: 100%;
    height: 62px;
    border: 1px solid #d9d9d2;
    border-radius: 22px;
    display: flex;
    align-items: center;
    padding: 0 18px;
    margin-bottom: 14px;
    background: #f8f7f2;
    transition: .3s;
}

.input-box:focus-within {
    border-color: #315d42;
    box-shadow: 0 0 0 3px #315d4215;
}

.input-box .icon {
    font-size: 23px;
    margin-right: 20px;
    color: #1c4934;
}

.input-box input {
    width: 100%;
    border: none;
    outline: none;
    background: transparent;
    font-size: 17px;
    color: #183d2d;
}

.eye {
    cursor: pointer;
    font-size: 21px;
    color: #777;
}

.options {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin: 20px 0 25px;
    font-size: 15px;
    color: #111;
}

.remember {
    display: flex;
    align-items: center;
    gap: 8px;
}

.remember input {
    accent-color: #204632;
    width: 19px;
    height: 19px;
}

a {
    text-decoration: none;
    color: #173d2c;
    font-weight: bold;
    cursor: pointer;
}

.main-btn {
    width: 100%;
    height: 63px;
    border: none;
    border-radius: 35px;
    background: linear-gradient(110deg, #173c29, #294b35);
    color: white;
    font-size: 20px;
    font-weight: bold;
    cursor: pointer;
    transition: .3s;
}

.main-btn:hover {
    transform: translateY(-3px);
    box-shadow: 0 7px 15px #173c2930;
}

.main-btn:disabled,
.google-btn:disabled {
    opacity: .6;
    cursor: wait;
}

.divider {
    display: flex;
    align-items: center;
    gap: 12px;
    margin: 17px 0;
    color: #555;
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
    height: 55px;
    border: 1px solid #1e3328;
    border-radius: 30px;
    background: transparent;
    font-size: 17px;
    cursor: pointer;
}

.google-icon {
    font-size: 22px;
    font-weight: bold;
    margin-right: 10px;
    color: #4285f4;
}

.bottom-text {
    margin-top: 28px;
    text-align: center;
    font-size: 16px;
    color: #111;
}

.bottom-text a {
    margin-left: 5px;
}

.signup {
    display: none;
}

.signup .top {
    width: 100%;
    margin-top: 65px;
    text-align: center;
}

.back {
    width: 55px;
    height: 55px;
    border-radius: 50%;
    border: 1px solid #ddd;
    background: white;
    font-size: 25px;
    cursor: pointer;
    display: block;
    margin-bottom: 35px;
}

.signup h2 {
    font-size: 36px;
    margin-bottom: 12px;
}

.signup .subtitle {
    font-size: 18px;
    line-height: 1.5;
    color: #333;
}

.signup .form {
    margin-top: 30px;
}

.signup .bottom-text {
    margin-top: 30px;
}

.decoration {
    position: absolute;
    bottom: 0;
    left: 0;
    width: 100%;
    height: 90px;
    background: linear-gradient(170deg, transparent 20%, #e4eedb 21%, #8eae78 75%, #315a39);
    clip-path: polygon(0 40%, 20% 60%, 45% 80%, 70% 50%, 100% 35%, 100% 100%, 0 100%);
}

@media(max-width: 900px) {
    body {
        padding: 15px;
    }

    .container {
        grid-template-columns: 1fr;
        max-width: 500px;
        gap: 25px;
    }

    .phone {
        min-height: 800px;
        padding: 25px 30px;
    }

    .logo {
        margin-top: 60px;
    }

    .signup .top {
        margin-top: 35px;
    }

    .signup {
        min-height: 850px;
    }
}

@media(max-width: 400px) {
    .phone {
        padding: 25px 22px;
    }

    .logo h1 {
        font-size: 35px;
    }

    .signup h2 {
        font-size: 29px;
    }
}
</style>
</head>

<body>

<div class="container">

<section class="phone login" id="login">

    <div class="logo">
        <div class="logo-icon">⌂🌿</div>
        <h1>Energy <span>Watch</span></h1>
        <p class="tagline">Monitor • Save • Live Green</p>
    </div>

    <div class="city"></div>

    <form class="form" onsubmit="loginUser(event)">

        <div class="input-box">
            <span class="icon">👤</span>
            <input type="email" id="loginEmail"
            placeholder="Email Address" required>
        </div>

        <div class="input-box">
            <span class="icon">🔒</span>
            <input type="password" id="loginPassword"
            placeholder="Password" required>
            <span class="eye"
            onclick="togglePassword('loginPassword',this)">◉</span>
        </div>

        <div class="options">
            <label class="remember">
                <input type="checkbox">
                Remember Me
            </label>

            <a onclick="forgotPassword()">Forgot Password?</a>
        </div>

        <button class="main-btn" id="loginButton" type="submit">
            Log In &nbsp; →
        </button>

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

    <form class="form" onsubmit="signupUser(event)">

        <div class="input-box">
            <span class="icon">👤</span>
            <input type="text" id="signupName"
            placeholder="Full Name" required>
        </div>

        <div class="input-box">
            <span class="icon">✉</span>
            <input type="email" id="signupEmail"
            placeholder="Email Address" required>
        </div>

        <div class="input-box">
            <span class="icon">🔒</span>
            <input type="password" id="signupPassword"
            placeholder="Password" required minlength="6">
            <span class="eye"
            onclick="togglePassword('signupPassword',this)">◉</span>
        </div>

        <div class="input-box">
            <span class="icon">🔒</span>
            <input type="password" id="confirmPassword"
            placeholder="Confirm Password" required minlength="6">
            <span class="eye"
            onclick="togglePassword('confirmPassword',this)">◉</span>
        </div>

        <button class="main-btn" id="signupButton" type="submit">
            Sign Up &nbsp; →
        </button>

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

<script>
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
</script>

<script type="module">

import {
    initializeApp
} from "https://www.gstatic.com/firebasejs/13.4.0/firebase-app.js";

import {
    getAuth,
    createUserWithEmailAndPassword,
    signInWithEmailAndPassword,
    sendPasswordResetEmail,
    updateProfile,
    GoogleAuthProvider,
    signInWithPopup
} from "https://www.gstatic.com/firebasejs/13.4.0/firebase-auth.js";

import {
    getDatabase,
    ref,
    set,
    onValue
} from "https://www.gstatic.com/firebasejs/13.4.0/firebase-database.js";

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

// INITIALIZE FIREBASE

const app = initializeApp(firebaseConfig);
const auth = getAuth(app);
const database = getDatabase(app);

// GOOGLE PROVIDER

const googleProvider = new GoogleAuthProvider();

googleProvider.setCustomParameters({
    prompt: "select_account"
});

// DATABASE CONNECTION CHECK

const connectedRef = ref(database, ".info/connected");

onValue(connectedRef, (snapshot) => {
    console.log(
        snapshot.val()
        ? "Firebase Database Connected!"
        : "Firebase Database Disconnected!"
    );
});

// SAVE USER PROFILE

async function saveUserProfile(user, name = "") {

    const profileRef = ref(
        database,
        "users/" + user.uid + "/profile"
    );

    await set(profileRef, {
        name: name || user.displayName || "",
        email: user.email || "",
        uid: user.uid,
        updatedAt: Date.now()
    });

}

// SIGN UP

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
            auth,
            email,
            password
        );

        await updateProfile(result.user, {
            displayName: name
        });

        await saveUserProfile(result.user, name);

        alert("Your account has been created successfully!");

        document.getElementById("signupPassword").value = "";
        document.getElementById("confirmPassword").value = "";

        showLogin();

    } catch (error) {

        console.error("Sign Up Error:", error);

        if (error.code === "auth/email-already-in-use") {
            alert("This email is already registered. Please Log In.");
        } else if (error.code === "auth/weak-password") {
            alert("Password must be at least 6 characters.");
        } else {
            alert("Sign Up Error: " + error.message);
        }

    } finally {
        button.disabled = false;
        button.textContent = "Sign Up →";
    }

};

// LOGIN

window.loginUser = async function(event) {

    event.preventDefault();

    const button = document.getElementById("loginButton");

    const email = document.getElementById("loginEmail").value.trim();
    const password = document.getElementById("loginPassword").value;

    button.disabled = true;
    button.textContent = "Logging in...";

    try {

        const result = await signInWithEmailAndPassword(
            auth,
            email,
            password
        );

        await saveUserProfile(result.user);

        alert("Welcome to Energy Watch!");

        console.log("Logged in user:", result.user.uid);

    } catch (error) {

        console.error("Login Error:", error);

        if (
            error.code === "auth/invalid-credential" ||
            error.code === "auth/wrong-password" ||
            error.code === "auth/user-not-found"
        ) {
            alert("Incorrect email or password.");
        } else {
            alert("Login Error: " + error.message);
        }

    } finally {
        button.disabled = false;
        button.textContent = "Log In →";
    }

};

// GOOGLE LOGIN

window.googleLogin = async function() {

    try {

        const result = await signInWithPopup(
            auth,
            googleProvider
        );

        await saveUserProfile(result.user);

        alert(
            "Welcome to Energy Watch, " +
            (result.user.displayName || "User") + "!"
        );

        console.log("Google Login Successful:", result.user.uid);

    } catch (error) {

        console.error("Google Login Error:", error);

        if (error.code === "auth/popup-closed-by-user") {
            alert("Google sign-in was cancelled.");
        } else if (error.code === "auth/unauthorized-domain") {
            alert("This website domain is not authorized in Firebase.");
        } else {
            alert("Google Login Error: " + error.message);
        }

    }

};

// FORGOT PASSWORD

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

        console.error("Password Reset Error:", error);

        alert("Password Reset Error: " + error.message);

    }

};

</script>

</body>
</html>
