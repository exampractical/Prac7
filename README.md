
# Practical 7 - Email Validator Using HTML, CSS and JavaScript

## a1.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
    <title>Email Validator</title>
    <link rel="stylesheet" href="style.css" />
</head>
<body>

    <div class="container">
        <h2>Email Validator</h2>
        <input type="text" id="email" placeholder="Enter email" oninput="validateEmail()">
        <button onclick="validateEmail()">Check</button>
        <p id="message"></p>
    </div>

    <script src="script.js"></script>
</body>
</html>
```

## style.css

```css
body {
    font-family: Arial, sans-serif;
    background: linear-gradient(135deg, #ff9ff3, #48dbfb);
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
}

.container {
    background-color: white;
    padding: 30px 40px;
    border-radius: 10px;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
    text-align: center;
    width: 320px;
}

h2 {
    color: #341f97;
    margin-bottom: 20px;
}

input {
    width: 100%;
    padding: 10px;
    margin: 15px 0;
    border: 2px solid #dfe6e9;
    border-radius: 5px;
    font-size: 16px;
    box-sizing: border-box;
}

button {
    width: 100%;
    background-color: #341f97;
    color: white;
    border: none;
    padding: 10px;
    border-radius: 5px;
    cursor: pointer;
    font-size: 16px;
}

button:hover {
    background-color: #2e86de;
}

#message {
    margin-top: 10px;
    font-weight: bold;
    white-space: nowrap;
}
```

## script.js

```javascript
function validateEmail() {
    let email = document.getElementById("email").value.trim();
    let message = document.getElementById("message");

    if (!email) return show("Please enter an email!", "red");

    let hasAt = email.includes("@");
    let hasDot = email.includes(".");

    // Missing symbols
    if (!hasAt && !hasDot)
        return show("Missing '@' and '.' !", "red");

    if (!hasAt)
        return show("Missing '@' symbol!", "red");

    if (!hasDot)
        return show("Missing '.' symbol!", "red");

    // Check Gmail spelling
    let [username, domainPart] = email.split("@");

    if (!username || !domainPart)
        return show("Invalid format!", "red");

    if (domainPart.startsWith("g") && !domainPart.startsWith("gmail.com")) {
        return show("⚠ Check Gmail spelling!", "orange");
    }

    // Valid
    return show("Valid Email!", "green");

    function show(text, color) {
        message.textContent = text;
        message.style.color = color;
    }
}
```
