<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Happy 16 Months!</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f0e4d7;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
      margin: 0;
      text-align: center;
      color: #4a3728;
    }
    h1 {
      font-size: 24px;
      margin-bottom: 10px;
    }
    #gameArea {
      position: relative;
      width: 90%;
      max-width: 400px;
      height: 300px;
      background-color: #d4c2a7;
      border-radius: 10px;
      overflow: hidden;
    }
    #capybara {
      position: absolute;
      width: 50px;
      cursor: pointer;
      transition: all 0.2s;
    }
    #score {
      font-size: 18px;
      margin: 10px 0;
    }
    #winScreen, #messageScreen, #giftScreen, #finalScreen {
      display: none;
      margin-top: 20px;
      background-color: #fff;
      padding: 15px;
      border-radius: 10px;
      box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
      max-width: 90%;
    }
    .gift-box {
      width: 60px;
      height: 60px;
      background-color: #ffcccc;
      border: 2px solid #ff9999;
      border-radius: 50%;
      display: inline-block;
      margin: 5px;
      cursor: pointer;
      text-align: center;
      line-height: 60px;
      font-size: 16px;
      color: #ff9999;
    }
    .gift-box:hover {
      background-color: #ff9999;
      color: white;
    }
    button {
      background-color: #8bc34a;
      color: white;
      padding: 10px 20px;
      border: none;
      border-radius: 5px;
      font-size: 16px;
      margin: 5px;
      cursor: pointer;
    }
    button:hover {
      background-color: #689f38;
    }
    p {
      font-size: 14px;
      line-height: 1.5;
    }
  </style>
</head>
<body>
  <h1>Happy 16 Months, Luvv! 🦫</h1>
  <p>Play to catch the capybara and win a surprise!</p>
  <div id="gameArea">
    <img id="capybara" src="https://i.postimg.cc/PJNv3KgD/IMG-20250417-112226.jpg" alt="Capybara">
  </div>
  <p id="score">Score: 0/5</p>
  <div id="winScreen">
    <h2>Congratulations, you won!</h2>
    <button onclick="showMessage()">Claim Your Gift</button>
  </div>
  <div id="messageScreen">
    <p>My Love,<br><br>
    Happy 16 Months to us! Looking back, I’m amazed at how much we’ve grown—16 months of love, laughter, and supporting each other through life’s ups and downs. Today, I want to share something I’ve been holding close since last night.<br><br>
    When you gave me that box of chocolates, it wasn’t just about how delicious they looked (though they are!). It was about how you always make me feel so special, even with the smallest gestures. I know how much thought you put into it, and it left me a little shy because you’re so generous—not just with gifts, but with your time and heart.<br><br>
    Those chocolates are more than a treat. They’re a reminder that you see me, even when I’m my quiet, awkward self. Every bite feels like your way of saying, “You’re worth it.” And you’re worth every smile you bring me, every dream we share, and every moment we build together.<br><br>
    These 16 months have been a warm, wonderful ride—like the sweetest chocolate melting slowly. I’m so proud of you for pushing to get fit with jogging, and I love how your curiosity about me makes every day brighter. Here’s to a lifetime of love that keeps getting sweeter.<br><br>
    Thank you for being my person. I love you—today, tomorrow, and always.<br><br>
    Forever yours,</p>
    <button onclick="showGifts()">Choose Your Gift!</button>
  </div>
  <div id="giftScreen">
    <h2>Pick Your Gift!</h2>
    <div class="gift-box" onclick="showGift(1)">❤️</div>
    <div class="gift-box" onclick="showGift(2)">❤️</div>
    <div class="gift-box" onclick="showGift(3)">❤️</div>
    <p id="gift1" style="display: none;">More than 3 Rounds of Bembang</p>
    <p id="gift2" style="display: none;">Home Date</p>
    <p id="gift3" style="display: none;">Outside Date</p>
  </div>
  <div id="finalScreen">
    <h2>Congratulations! Loving you always 😘</h2>
  </div>
  <script>
    let score = 0;
    const capybara = document.getElementById('capybara');
    const scoreDisplay = document.getElementById('score');
    const gameArea = document.getElementById('gameArea');
    const winScreen = document.getElementById('winScreen');

    function moveCapybara() {
      const maxX = gameArea.offsetWidth - capybara.offsetWidth;
      const maxY = gameArea.offsetHeight - capybara.offsetHeight;
      const newX = Math.random() * maxX;
      const newY = Math.random() * maxY;
      capybara.style.left = newX + 'px';
      capybara.style.top = newY + 'px';
    }

    capybara.addEventListener('click', () => {
      score++;
      scoreDisplay.textContent = `Score: ${score}/5`;
      moveCapybara();
      if (score >= 5) {
        gameArea.style.display = 'none';
        scoreDisplay.style.display = 'none';
        winScreen.style.display = 'block';
      }
    });

    setInterval(moveCapybara, 1000);
    moveCapybara();

    function showMessage() {
      winScreen.style.display = 'none';
      document.getElementById('messageScreen').style.display = 'block';
    }

    function showGifts() {
      document.getElementById('messageScreen').style.display = 'none';
      document.getElementById('giftScreen').style.display = 'block';
    }

    function showGift(giftId) {
      document.getElementById('giftScreen').style.display = 'none';
      document.getElementById(`gift${giftId}`).style.display = 'block';
      setTimeout(() => {
        document.getElementById(`gift${giftId}`).style.display = 'none';
        document.getElementById('finalScreen').style.display = 'block';
      }, 3000); // Show gift for 3 seconds before final message
    }
  </script>
</body>
</html>
