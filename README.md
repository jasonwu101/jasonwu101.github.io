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
            max-width: 500px;
        }

        .hidden {
            display: none;
        }

        input[type="password"] {
            padding: 0.5rem;
            font-size: 1rem;
            margin: 1rem 0;
            width: calc(100% - 2rem);
            border: 1px solid #ccc;
            border-radius: 5px;
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

        #password-page {
            margin-bottom: 6rem; /* Adjust to the desired space */
        }

        .scroll-container {
            margin-top: 1rem;
            padding: 2rem;
            background: #fff;
            border: 1px solid #ddd;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            max-width: 600px;
            margin: 2rem auto;
            overflow-y: auto;
        }

        ol {
            text-align: left;
            margin: 0 auto;
            line-height: 1.8;
            padding-left: 1rem;
        }

        @media (max-width: 768px) {
            .container {
                width: 90%;
            }

            .scroll-container {
                width: 90%;
            }
        }

        #easter-egg {
            visibility: hidden;
            cursor: pointer;
            font-size: 1.5rem;
            margin-top: 2rem;
        }

        #hidden-number {
            display: none;
            font-weight: bold;
        }
    </style>
</head>
<body>
    <!-- Introduction Page -->
    <div id="intro-page" class="container">
        <h2>Merry Christmas!</h2>
        <p>I have your present but it will take some effort.</p>
        <p>Are you ready?</p>
        <button onclick="showPasswordPage()">Yes</button>
        <button onclick="notReady()">No</button>
    </div>

    <!-- Password Page -->
    <div class="container hidden" id="password-page">
        <h2>Password Protected</h2>
        <p>Please enter the password to access the next screen.</p>
        <input type="password" id="password-input" placeholder="Enter password" aria-label="Password Input">
        <button onclick="checkPassword()">Submit</button>
        <p id="error-message-1" style="color: red; display: none;" aria-live="polite"></p>
        <p id="error-message-2" style="color: red; display: none;" aria-live="polite"></p>
        <p id="error-message-3" style="color: red; display: none;" aria-live="polite"></p>
    </div>

    <!-- Success Page -->
    <div id="content-page" class="container hidden">
        <h2>Congratulations!</h2>
        <p>You have successfully accessed the page.</p>
        <p id="easter-egg" onclick="revealEasterEgg()">Hover and click me!</p>
        <span id="hidden-number">4111</span>
    </div>

    <!-- Scrollable Section with Questions -->
    <div class="scroll-container hidden" id="questions-section">
        <h2>The password is 21 characters</h2>
        <p>Below are 21 questions and the first letter of each answer is one part of the password in numerical order. </p>
        <ol>
            <li>If someone buys 10 BTC at once they are called a ___ ?</li>
            <li>What animal do most people think of when they hear Australia?</li>
            <li>Which Fortnite Season did I start playing?</li>
            <li>This state has a lot of hurricanes.</li>
            <li>777 is a ____ number.</li>
            <li>A diet where you eat poultry and not consume red meat or pork.</li>
            <li>An app where you can buy stocks (hint: feather).</li>
            <li>Which NFT was once worth more than 1 BTC?</li>
            <li>Used to be called Twitter.</li>
            <li>What is your dad’s favorite country (In Europe)?</li>
            <li>Which shoe brand made me the most money?</li>
            <li>What town is your mom born in?</li>
            <li>Which campus was feature in Black Panther: Wakanda Forever?</li>
            <li>China Garden is giving away free ___ to customer this year.</li>
            <li>What car brand does my dad drive?</li>
            <li>What year was I born?</li>
            <li>Who gave John Wick his first dog?</li>
            <li>Anthony wants to go to ___ high school.</li>
            <li>What is my main major at Purdue University?</li>
            <li>What is this website being hosted on?</li>
            <li>What is your mom’s dream car?</li>
        </ol>
    </div>

    <script>
        const correctPassword = "WKTFLPRPXSNGMCHTHWMGC"; // Store password securely on the server for production.
        let errorIndex = 0; // Tracks the current error message

        function showPasswordPage() {
            document.getElementById("intro-page").classList.add("hidden");
            document.getElementById("password-page").classList.remove("hidden");
            document.getElementById("questions-section").classList.remove("hidden");
        }

        function notReady() {
            alert("Take your time and come back when you are ready!");
        }

        function checkPassword() {
            const input = document.getElementById("password-input").value;
            const errorMessages = [
                { id: "error-message-1", text: "Incorrect password. Try again." },
                { id: "error-message-2", text: "Wrong again LOL." },
                { id: "error-message-3", text: "Did you type in all CAPS?" }
            ];
            const passwordPage = document.getElementById("password-page");
            const contentPage = document.getElementById("content-page");

            // Hide all error messages
            errorMessages.forEach(msg => {
                document.getElementById(msg.id).style.display = "none";
            });

            if (input === correctPassword) {
                passwordPage.classList.add("hidden");
                contentPage.classList.remove("hidden");
                document.getElementById("questions-section").classList.add("hidden");
            } else {
                // Show the current error message
                const currentMessage = errorMessages[errorIndex];
                const errorElement = document.getElementById(currentMessage.id);
                errorElement.textContent = currentMessage.text;
                errorElement.style.display = "block";

                // Move to the next error message
                errorIndex = (errorIndex + 1) % errorMessages.length;
            }
        }

        // Easter Egg reveal function
        function revealEasterEgg() {
            const hiddenNumber = document.getElementById("hidden-number");
            hiddenNumber.style.display = "inline"; // Show the hidden number when clicked
            alert("You found the Easter egg: 4111!");
        }

        // Make the Easter egg visible on hover
        document.getElementById("easter-egg").addEventListener("mouseover", function () {
            this.style.visibility = "visible";
        });
    </script>
</body>
</html>
