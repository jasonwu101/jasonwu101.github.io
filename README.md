<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Days We've Been Dating</title>
  <style>
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
      margin: 0;
      background-color: #ffe6e6;
      color: #333;
    }
    h1 {
      font-size: 2.5rem;
    }
    p {
      font-size: 2rem;
      margin-top: 0.5rem;
    }
    .heart {
      color: red;
      font-size: 3rem;
      animation: pulse 1s infinite alternate;
    }
    @keyframes pulse {
      to {
        transform: scale(1.2);
      }
    }
  </style>
</head>
<body>
  <h1>💕 We've been dating for:</h1>
  <p id="days">...</p>
  <div class="heart">❤️</div>

  <script>
    const startDate = new Date("2025-03-08");
    const today = new Date();

    const oneDay = 1000 * 60 * 60 * 24;
    const diffDays = Math.floor((today - startDate) / oneDay);

    document.getElementById("days").textContent = `${diffDays} days`;
  </script>
</body>
</html>
