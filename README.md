<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Kaylee's Countdown Hub</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Quicksand:wght@500&display=swap');

    body {
      font-family: 'Quicksand', sans-serif;
      background: linear-gradient(to right, #fcefee, #e8f0ff);
      margin: 0;
      padding: 40px 20px;
      display: flex;
      flex-direction: column;
      align-items: center;
    }

    h1 {
      font-size: 2.2rem;
      color: #6c4a84;
      margin-bottom: 10px;
    }

    .countdown-container {
      display: flex;
      flex-direction: column;
      gap: 30px;
      max-width: 600px;
      width: 100%;
    }

    .card {
      background: white;
      padding: 25px 30px;
      border-radius: 2rem;
      box-shadow: 0 8px 24px rgba(0, 0, 0, 0.1);
      text-align: center;
    }

    .card h2 {
      margin: 0 0 10px;
      color: #ff7aa2;
      font-size: 1.5rem;
    }

    .countdown {
      font-size: 1.4rem;
      color: #444;
    }

    .highlight {
      font-weight: bold;
      color: #ff7aa2;
    }
  </style>
</head>
<body>
  <h1>Kaylee's Countdown Hub</h1>

  <div class="countdown-container" id="countdownContainer">
    <!-- Countdown cards will be generated here -->
  </div>

  <script>
    const events = [
      {
        title: "🎓 Commencement Ceremony (5/23/25)",
        date: "May 23, 2025 00:00:00",
        id: "ceremonyCountdown"
      },
      {
        title: "✅ MBA Graduation (8/8/25)",
        date: "August 8, 2025 00:00:00",
        id: "gradCountdown"
      },
      {
        title: "💍 Wedding Day (8/15/26)",
        date: "August 15, 2026 00:00:00",
        id: "weddingCountdown"
      }
    ];

    const countdownContainer = document.getElementById("countdownContainer");

    function calculateDaysLeft(dateStr) {
      const now = new Date().getTime();
      const target = new Date(dateStr).getTime();
      return Math.floor((target - now) / (1000 * 60 * 60 * 24));
    }

    // Sort by least days left
    events.sort((a, b) => calculateDaysLeft(a.date) - calculateDaysLeft(b.date));

    // Generate countdown cards
    events.forEach(event => {
      const card = document.createElement("div");
      card.className = "card";

      const heading = document.createElement("h2");
      heading.textContent = event.title;

      const countdownDiv = document.createElement("div");
      countdownDiv.className = "countdown";
      countdownDiv.id = event.id;
      countdownDiv.textContent = "Loading...";

      card.appendChild(heading);
      card.appendChild(countdownDiv);
      countdownContainer.appendChild(card);
    });

    // Function to update countdown
    function setCountdown(elementId, targetDateStr) {
      const update = () => {
        const targetDate = new Date(targetDateStr).getTime();
        const now = new Date().getTime();
        const timeLeft = targetDate - now;

        if (timeLeft < 0) {
          document.getElementById(elementId).innerHTML = "🎉 It's here!";
          return;
        }

        const days = Math.floor(timeLeft / (1000 * 60 * 60 * 24));
        const hours = Math.floor((timeLeft % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
        const minutes = Math.floor((timeLeft % (1000 * 60 * 60)) / (1000 * 60));
        const seconds = Math.floor((timeLeft % (1000 * 60)) / 1000);

        document.getElementById(elementId).innerHTML =
          `<span class="highlight">${days}</span> days 
           <span class="highlight">${hours}</span> hours 
           <span class="highlight">${minutes}</span> minutes 
           <span class="highlight">${seconds}</span> seconds`;
      };

      update(); // Initial call
      setInterval(update, 1000);
    }

    // Initialize all countdowns
    events.forEach(event => {
      setCountdown(event.id, event.date);
    });
  </script>
</body>
</html>
