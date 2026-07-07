<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Kids Nursery Rhymes</title>
  <style>
    body {
      font-family: "Comic Sans MS", sans-serif;
      text-align: center;
      background: linear-gradient(to bottom, #fceabb, #f8b500);
      margin: 0;
      padding: 0;
    }
    header {
      background: #ff69b4;
      color: white;
      padding: 20px;
      font-size: 32px;
    }
    .rhyme-box {
      margin: 30px auto;
      padding: 20px;
      width: 70%;
      background: #fff;
      border-radius: 15px;
      box-shadow: 0 4px 8px rgba(0,0,0,0.2);
    }
    .rhyme-title {
      font-size: 28px;
      color: #333;
    }
    .lyrics {
      margin-top: 15px;
      font-size: 20px;
      white-space: pre-line;
      color: #444;
    }
    button {
      margin: 10px;
      padding: 12px 25px;
      font-size: 18px;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      background: #4CAF50;
      color: white;
    }
    button:hover {
      background: #45a049;
    }
  </style>
</head>
<body>
  <header>🌈 Kids Nursery Rhymes 🎵</header>

  <div class="rhyme-box">
    <div class="rhyme-title" id="rhymeTitle"></div>
    <div class="lyrics" id="lyrics"></div>
    <audio id="audioPlayer" controls></audio>
    <div>
      <button onclick="prevRhyme()">⬅️ Previous</button>
      <button onclick="nextRhyme()">Next ➡️</button>
    </div>
  </div>

  <script>
    const rhymes = [
      {
        title: "Rainbow Song",
        lyrics: "Red and orange, yellow too,\nGreen and blue, indigo hue,\nViolet shines at the end,\nRainbow colors, all my friends!",
        sound: "sounds/rainbow_song.mp3"
      },
      {
        title: "Twinkle Twinkle",
        lyrics: "Twinkle, twinkle, little star,\nHow I wonder what you are!\nUp above the world so high,\nLike a diamond in the sky.",
        sound: "sounds/twinkle_song.mp3"
      },
      {
        title: "ABC Song",
        lyrics: "A B C D E F G,\nCome and sing along with me!\nH I J K L M N,\nLearning letters is such fun!",
        sound: "sounds/abc_song.mp3"
      }
    ];

    let currentIndex = 0;
    const rhymeTitle = document.getElementById("rhymeTitle");
    const lyrics = document.getElementById("lyrics");
    const audioPlayer = document.getElementById("audioPlayer");

    function showRhyme(index) {
      const rhyme = rhymes[index];
      rhymeTitle.textContent = rhyme.title;
      lyrics.textContent = rhyme.lyrics;
      audioPlayer.src = rhyme.sound;
      audioPlayer.play();
    }

    function nextRhyme() {
      currentIndex = (currentIndex + 1) % rhymes.length;
      showRhyme(currentIndex);
    }

    function prevRhyme() {
      currentIndex = (currentIndex - 1 + rhymes.length) % rhymes.length;
      showRhyme(currentIndex);
    }

    // Show first rhyme on load
    showRhyme(currentIndex);
  </script>
</body>
</html>
