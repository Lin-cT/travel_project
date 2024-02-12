---
permalink: /signup
---
<html>
<head>
    <title>Sign Up</title>
</head>
<body>
<div class="form-container">
    <h2 id="pageTitle">Sign Up</h2>
    <form>
        <input type="text" id="name" class="type" placeholder="Full Name"><br>
        <input type="text" id="user" class="type" placeholder="Username"><br>
        <input type="password" id="pass" class="type" placeholder="Password">
    </form>
    <button class="submit" onclick="signup()">Sign Up</button>
    <p id="error"></p>
    <button onclick="switchToLogin()">Switch to Login</button>
</div>
</body>
<script>
function switchToLogin() {
    window.location.href = "http://127.0.0.1:4200/travel_project/login";
}
function signup() {
    data = {
        "name": document.getElementById("name").value,
        "uid": document.getElementById("user").value,
        "password": document.getElementById("pass").value,
        }
    let options = {
    method: 'POST',
    headers: {
        'Content-Type':
            'application/json;charset=utf-8'
    },
    body: JSON.stringify(data)
}
    let sign_up = fetch('http://127.0.0.1:8086/api/users/', options);
    sign_up.then(response => {
        if (response.status === 200) {
            window.location.href = "http://127.0.0.1:4200/travel_project/login"
        }
        else if (response.status === 400) {
            document.getElementById("error").innerHTML = "You already have an account! Go to the login page."
        }
    }
        ) 
}
</script>
</html>