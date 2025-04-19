
<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Untuk Kamu yang Spesial</title>
  <style>
    body {
      margin: 0;
      font-family: 'Arial', sans-serif;
      background: linear-gradient(135deg, #f2f2f2, #e6e6e6);
      color: #333;
      overflow: hidden;
      text-align: center;
    }
    #startBtn {
      position: absolute;
      top: 40%;
      left: 50%;
      transform: translate(-50%, -50%);
      font-size: 20px;
      padding: 15px 30px;
      background: #ff6f61; /* Soft Coral */
      color: white;
      border: none;
      border-radius: 20px;
      cursor: pointer;
      transition: background 0.3s;
    }
    #startBtn:hover {
      background: #ff4c3e; /* Darker Coral */
    }
    #mainContent {
      display: none;
      padding: 20px;
    }
    .hearts {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
      z-index: -1;
    }
    .heart {
      position: absolute;
      width: 20px;
      height: 20px;
      background: #ff1e63; /* Bright Pink */
      transform: rotate(45deg);
      animation: fall 5s linear infinite;
    }
    .heart:before,
    .heart:after {
      content: "";
      position: absolute;
      width: 20px;
      height: 20px;
      background: #ff1e63; /* Bright Pink */
      border-radius: 50%;
    }
    .heart:before {
      top: -10px;
      left: 0;
    }
    .heart:after {
      left: -10px;
      top: 0;
    }
    @keyframes fall {
      100% {
        transform: translateY(100vh) rotate(360deg);
        opacity: 0;
      }
    }
    h1 {
      color: #2c3e50; /* Dark Navy */
    }
    h2 {
      color: #8e44ad; /* Dark Purple */
    }
    input[type="text"] {
      padding: 10px;
      margin: 10px 0;
      border: 2px solid #3498db; /* Soft Blue */
      border-radius: 5px;
      width: 60%;
    }
    input[type="text"]:focus {
      border-color: #2980b9; /* Darker Blue */
      outline: none;
    }
    button {
      padding: 10px 20px;
      background: #2ecc71; /* Soft Green */
      border: none;
      border-radius: 5px;
      color: white;
      cursor: pointer;
      transition: background 0.3s;
    }
    button:hover {
      background: #27ae60; /* Darker Green */
    }
    #countdown {
      font-size: 24px;
      margin-top: 20px;
      color: #e67e22; /* Carrot Orange */
    }
    img {
      height: 200px;
      padding: 30px;
      width: auto;
      max-width: 90%;
      border-radius: 15px;
      transition: transform 0.3s;
    }
    img:hover {
      transform: scale(1.05);
    }
  </style>
</head>
<body>

<button id="startBtn" aria-label="Buka Halaman Cinta">Buka Halaman Cinta</button>

<main id="mainContent" role="main">
  <h1>Hai <span id="namaTarget">Bayik</span>!</h1>
  <input type="text" id="inputNama" placeholder="Masukkan nama pacar kamu..." aria-label="Nama pacar" />
  <button id="saveNameBtn">Simpan Nama</button>

  <h2 id="rayuan">Klik tombol untuk rayuan manis!</h2>
  <button id="rayuBtn">Rayu Aku</button>

  <div id="countdown"></div>

  <div class="hearts" id="heartsContainer"></div>
  <div>
    <img src="n/1.jpg" alt="Gambar 1">
    <img src="n/2.jpg" alt="Gambar 2">
    <img src="n/3.jpg" alt="Gambar 3">
  </div>

  <audio src="n/song.mp3" controls autoplay></audio>
</main>

<script>
  const btn = document.getElementById("startBtn");
  const content = document.getElementById("mainContent");
  const heartsContainer = document.getElementById("heartsContainer");
  const inputField = document.getElementById("inputNama");
  const saveNameBtn = document.getElementById("saveNameBtn");
  const rayuBtn = document.getElementById("rayuBtn");

  btn.addEventListener("click", () => {
    btn.style.display = "none";
    content.style.display = "block";
    createHearts();
  });

  saveNameBtn.addEventListener("click", setNama);
  rayuBtn.addEventListener("click", rayuanRandom);

  inputField.addEventListener("keypress", function(event) {
    if (event.key === "Enter") {
      setNama();
    }
  });

  function setNama() {
    const nama = inputField.value.trim();
    document.getElementById("namaTarget").innerText = nama || "Sayang";
  }

  function rayuanRandom() {
    const rayuan = [
      "Kamu tuh kayak matematika, bikin aku mikir terus...",
      "Kalau kamu jadi bintang, aku rela jadi langitnya.",
      "Bersamamu waktu terasa cepat, tanpamu... rasanya lama banget.",
      "Aku nggak butuh peta, soalnya hatiku udah nemu tujuan—kamu."
    ];
    const pilih = rayuan[Math.floor(Math.random() * rayuan.length)];
    document.getElementById("rayuan").innerText = pilih;
  }

  function createHearts() {
    for (let i = 0; i < 30; i++) {
      let heart = document.createElement("div");
      heart.className = "heart";
      heart.style.left = Math.random() * 100 + "vw";
      heart.style.animationDuration = (Math.random() * 3 + 2) + "s";
      heartsContainer.appendChild(heart);
    }
  }

  function updateCountdown() {
    const targetDate = new Date("2023-08-20");
    const now = new Date();
    const diff = now - targetDate;
    const days = Math.floor(diff / (1000 * 60 * 60 * 24));
    document.getElementById("countdown").innerText = `Sejak kita bertemu waktu kelas 10`;
  }
  
  updateCountdown();
  setInterval(updateCountdown, 86400000);
</script>
</body>
</html>
