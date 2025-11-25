<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Dating Days Counter</title>
  <style>
    body {
      background-color: #ffe6e6;
      color: #333;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      margin: 0;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
      text-align: center;
    }

    h1 {
      font-size: 2rem;
      margin-bottom: 0.5rem;
    }

    #days, #months {
      font-size: 2.2rem;
      font-weight: bold;
      margin: 0.2rem 0;
    }

    .heart {
      font-size: 3rem;
      margin-top: 0.5rem;
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
  <h1>We've been dating for:</h1>
  <div id="days"></div>
  <div id="months"></div>
  <div class="heart">❤️</div>

  <script>
    const startDate = new Date("2025-03-08");
    const today = new Date();

    const oneDay = 1000 * 60 * 60 * 24;
    const diffDays = Math.floor((today - startDate) / oneDay);

    // Months counter (approximate: actual month diff based on calendar)
    let diffMonths =
      (today.getFullYear() - startDate.getFullYear()) * 12 +
      (today.getMonth() - startDate.getMonth());

    // Adjust if the day of the month hasn't been reached yet
    if (today.getDate() < startDate.getDate()) {
      diffMonths--;
    }

    document.getElementById("days").textContent = `${diffDays} days`;
    document.getElementById("months").textContent = `${diffMonths} months`;
  </script>
</body>
</html>
