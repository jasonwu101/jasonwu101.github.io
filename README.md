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
            margin: 0.5rem;
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
        <!-- Introduction Page -->
        <div id="intro-page">
            <h2>Merry Christmas!</h2>
            <p>I have your present but it will take some effort.</p>
            <p>Are you ready?</p>
            <button onclick="showPasswordPage()">Yes</button>
            <button onclick="notReady()">No</button>
        </div>

        <!-- Password Page -->
        <div id="password-page" class="hidden">
            <h2>Password Protected</h2>
            <p>Please enter the password to access the next screen.</p>
            <input type="password" id="password-input" placeholder="Enter password">
            <button onclick="checkPassword()">Submit</button>
            <p id="error-message" style="color: red; display: none;">Incorrect password. Try again.</p>
        </div>

        <!-- Not Ready Page -->
        <div id="not-ready-page" class="hidden">
            <h2>Take your time!</h2>
            <p>Come back when you're ready for the challenge.</p>
            <button onclick="goBackToIntro()">Back</button>
        </div>

        <!-- Success Page -->
        <div id="content-page" class="hidden">
            <h2>Congratulations!</h2>
            <p>You have successfully accessed the page.</p>
        </div>
    </div>

    <script>
        const correctPassword = "mysecurepassword";
        let errorToggle = true;

        function showPasswordPage() {
            document.getElementById("intro-page").classList.add("hidden");
            document.getElementById("password-page").classList.remove("hidden");
        }

        function notReady() {
            document.getElementById("intro-page").classList.add("hidden");
            document.getElementById("not-ready-page").classList.remove("hidden");
        }

        function goBackToIntro() {
            document.getElementById("not-ready-page").classList.add("hidden");
            document.getElementById("intro-page").classList.remove("hidden");
        }

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
