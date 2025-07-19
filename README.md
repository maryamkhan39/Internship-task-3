
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Contact Us</title>
    <link rel="stylesheet" href="styles.css">
    <link href="https:                                                                                                 
</head>
<body>
    <div class="container">
        <h1>Contact Us</h1>
        <form id="contact-form">
            <div class="form-group">
                <label for="fullName">Full Name:</label>
                <input type="text" id="fullName" name="fullName" required>
                <span class="error" id="fullNameError"></span>
            </div>
            <div class="form-group">
                <label for="email">Email:</label>
                <input type="email" id="email" name="email" required>
                <span class="error" id="emailError"></span>
            </div>
            <div class="form-group">
                <label for="message">Message:</label>
                <textarea id="message" name="message" required></textarea>
                <span class="error" id="messageError"></span>
            </div>
            <button type="submit">Submit</button>
            <p id="success-message"></p>
        </form>
    </div>

    <script src="script.js"></script>
</body>
</html>

### CSS (styles.css)
body {
    font-family: 'Open Sans', sans-serif;
    background-color: #f4f4f4;
}

.container {
    width: 50%;
    margin: 40px auto;
    padding: 20px;
    background-color: #fff;
    border: 1px solid #ddd;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

h1 {
    text-align: center;
}

.form-group {
    margin-bottom: 20px;
}

label {
    display: block;
    margin-bottom: 10px;
}

input, textarea {
    width: 100%;
    padding: 10px;
    margin-bottom: 10px;
    border: 1px solid #ccc;
}

button[type="submit"] {
    background-color: #4CAF50;
    color: #fff;
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}

button[type="submit"]:hover {
    background-color: #3e8e41;
}

.error {
    color: #f44336;
    font-size: 12px;
}

#success-message {
    color: #4CAF50;
    font-size: 16px;
    text-align: center;
}

### JavaScript (script.js)
const form = document.getElementById('contact-form');
const fullNameInput = document.getElementById('fullName');
const emailInput = document.getElementById('email');
const messageInput = document.getElementById('message');
const successMessage = document.getElementById('success-message');

form.addEventListener('submit', (e) => {
    e.preventDefault();

    const fullName = fullNameInput.value.trim();
    const email = emailInput.value.trim();
    const message = messageInput.value.trim();

    let isValid = true;

    if (fullName === '') {
        document.getElementById('fullNameError').innerText = 'Full name is required';
        isValid = false;
    } else {
        document.getElementById('fullNameError').innerText = '';
    }

    if (email === '') {
        document.getElementById('emailError').innerText = 'Email is required';
        isValid = false;
    } else if (!validateEmail(email)) {
        document.getElementById('emailError').innerText = 'Invalid email format';
        isValid = false;
    } else {
        document.getElementById('emailError').innerText = '';
    }

    if (message === '') {
        document.getElementById('messageError').innerText = 'Message is required';
        isValid = false;
    } else {
        document.getElementById('messageError').innerText = '';
    }

    if (isValid) {
        successMessage.innerText = 'Thank you for contacting us!';
        form.reset();
        setTimeout(() => {
            successMessage.innerText = '';
        }, 3000);
