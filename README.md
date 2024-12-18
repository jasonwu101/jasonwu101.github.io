<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Password Protected Page</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f9;
            color: #333;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }

        .container {
            text-align: center;
            background: #fff;
            padding: 2rem;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }

        input[type="password"] {
            padding: 0.5rem;
            font-size: 1rem;
            margin: 1rem 0;
            width: 80%;
        }

        button {
            padding: 0.5rem 1rem;
            font-size: 1rem;
            background-color: #333;
            color: #fff;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }

        button:hover {
            background-color: #555;
        }

        .hidden {
            display: none;
        }
    </style>
</head>
<body>
    <div class="container">
        <div id="password-page">
            <h2>Password Protected</h2>
            <p>Please enter the password to access the next screen. </p>
            <input type="password" id="password-input" placeholder="Enter password">
            <button onclick="checkPassword()">Submit</button>
            <p id="error-message" style="color: red; display: none;">Incorrect password. Try again.</p>
        </div>

        <div id="content-page" class="hidden">
            <h2>Congrations yoou finally figured out the password. </h2>
            <p>You have successfully accessed the page.</p>
        </div>
    </div>

    <script>
        const correctPassword = "password";
        let errorToggle = true;

        function checkPassword() {
            const input = document.getElementById("password-input").value;
            const errorMessage = document.getElementById("error-message");
            const passwordPage = document.getElementById("password-page");
            const contentPage = document.getElementById("content-page");

            if (input === correctPassword) {
                passwordPage.classList.add("hidden");
                contentPage.classList.remove("hidden");
            } else {
                // Alternate error messages
                errorMessage.textContent = errorToggle ? "Incorrect password. Try again." : "Wrong again LOL";
                errorToggle = !errorToggle;
                errorMessage.style.display = "block";
            }
        }
    </script>
</body>
</html>
