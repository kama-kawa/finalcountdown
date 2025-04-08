 <!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Countdown to August 8, 2025</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Quicksand:wght@500&display=swap');

    body {
      font-family: 'Quicksand', sans-serif;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
      margin: 0;
      background: linear-gradient(to right, #fcefee, #e8f0ff);
    }

    h1 {
      font-size: 2rem;
      margin-bottom: 20px;
      color: #6c4a84;
    }

    #countdown {
      font-size: 1.8rem;
      background: white;
      padding: 30px 40px;
      border-radius: 2rem;
      box-shadow: 0 8px 24px rgba(0, 0, 0, 0.1);
      color: #444;
      text-align: center;
    }

    .highlight {
      color: #ff7aa2;
      font-weight: bold;
    }
  </style>
</head>
<body>
  <h1>💍 Countdown to <span class="highlight">August 8, 2025</span></h1>
  <div id="countdown">Loading...</div>

  <script>
    const countdown = () => {
      const targetDate = new Date("August 8, 2025 00:00:00").getTime();
      const now = new Date().getTime();
      const timeLeft = targetDate - now;

      const days = Math.floor(timeLeft / (1000 * 60 * 60 * 24));
      const hours = Math.floor((timeLeft % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
      const minutes = Math.floor((timeLeft % (1000 * 60 * 60)) / (1000 * 60));
      const seconds = Math.floor((timeLeft % (1000 * 60)) / 1000);

      document.getElementById("countdown").innerHTML =
        `<span class="highlight">${days}</span> days 
         <span class="highlight">${hours}</span> hours 
         <span class="highlight">${minutes}</span> minutes 
         <span class="highlight">${seconds}</span> seconds`;

      if (timeLeft < 0) {
        document.getElementById("countdown").innerHTML = "🎉 It's here, CEO!";
      }
    };

    setInterval(countdown, 1000);
  </script>
</body>
</html>
