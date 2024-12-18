<!DOCTYPE html>
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
            margin: 0;
            padding: 0;
        }

        .container {
            text-align: center;
            background: #fff;
            padding: 2rem;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            margin: 2rem auto;
            width: 80%;
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
            margin-top: 1rem;
        }

        button:hover {
            background-color: #555;
        }

        .hidden {
            display: none;
        }

        .scroll-container {
            margin-top: 2rem;
            padding: 1.5rem;
            background: #fff;
            border: 1px solid #ddd;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }

        ol {
            text-align: left;
            margin: 0 auto;
            width: 80%;
            line-height: 1.8;
        }
    </style>
</head>
<body>
    <div class="container">
        <div id="password-page">
            <h2>Password Protected</h2>
            <p>Please enter the password to access the next screen.</p>
            <input type="password" id="password-input" placeholder="Enter password">
            <button onclick="checkPassword()">Submit</button>
            <p id="error-message" style="color: red; display: none;">Incorrect password. Try again.</p>
        </div>

        <div id="content-page" class="hidden">
            <h2>Congratulations!</h2>
            <p>You have successfully accessed the page.</p>
        </div>
    </div>

    <!-- Scrollable Section with Questions -->
    <div class="scroll-container">
        <h2>The password is 21 characters</h2>
        <p>Below are 21 questions and the first letter of each answer is one part of the password:</p>
        <ol>
            <li>What is the capital of France?</li>
            <li>Who wrote "To Kill a Mockingbird"?</li>
            <li>What is the chemical symbol for Gold?</li>
            <li>Which planet is known as the Red Planet?</li>
            <li>What is the largest mammal in the world?</li>
            <li>What language is primarily spoken in Brazil?</li>
            <li>Who painted the Mona Lisa?</li>
            <li>What is the currency of Japan?</li>
            <li>What is the boiling point of water in Celsius?</li>
            <li>Which animal is known as the King of the Jungle?</li>
            <li>What is the smallest prime number?</li>
            <li>Who discovered gravity?</li>
            <li>What is the name of the largest ocean?</li>
            <li>What is the square root of 144?</li>
            <li>Which country is known as the Land of the Rising Sun?</li>
            <li>What is the fastest land animal?</li>
            <li>Who is the author of the Harry Potter series?</li>
            <li>Which gas do plants primarily take in during photosynthesis?</li>
            <li>What is the hardest natural substance?</li>
            <li>What is the main ingredient in guacamole?</li>
            <li>Which bird is known for its impressive mimicry skills?</li>
        </ol>
    </div>

    <script>
        const correctPassword = "mysecurepassword";
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
                errorMessage.textContent = errorToggle ? "Incorrect password. Try again." : "Wrong again LOL";
                errorToggle = !errorToggle;
                errorMessage.style.display = "block";
            }
        }
    </script>
</body>
</html>
