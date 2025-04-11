<code>
<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Alpin Developer Payment</title>
  <link rel="icon" href="https://files.catbox.moe/y83vkl.jpg" type="image/png"/>
  <style>
    /* Reset dan gaya dasar */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }

    body {
      background: #f0f2f5;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }

    /* Animasi loading */
    #loading {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: white;
      display: flex;
      justify-content: center;
      align-items: center;
      z-index: 9999;
    }

    .spinner {
      border: 8px solid blue;
      border-top: 8px solid cyan;
      border-radius: 50%;
      width: 60px;
      height: 60px;
      animation: spin 1s linear infinite;
    }

    @keyframes spin {
      0% { transform: rotate(0deg); }
      100% { transform: rotate(360deg); }
    }

    /* Kontainer utama */
    #main {
      display: none;
      flex-direction: column;
      align-items: center;
      background: #fff;
      padding: 30px;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }

    h1 {
      margin-bottom: 20px;
      color: #333;
    }

    .payment-method {
      margin: 10px 0;
      text-align: center;
    }

    .payment-method p {
      margin-bottom: 5px;
      font-weight: bold;
    }

    .payment-method input {
      width: 200px;
      padding: 8px;
      margin-bottom: 5px;
      border: 1px solid #ccc;
      border-radius: 5px;
      text-align: center;
    }

    .payment-method button {
      padding: 5px 10px;
      margin-left: 5px;
      border: none;
      background-color: #3498db;
      color: #fff;
      border-radius: 5px;
      cursor: pointer;
    }

    .qr-section {
      margin: 20px 0;
      text-align: center;
    }

    .qr-section img {
      width: 150px;
      height: 150px;
      margin-bottom: 10px;
    }

    .qr-section a {
      display: inline-block;
      padding: 8px 12px;
      background-color: #2ecc71;
      color: #fff;
      text-decoration: none;
      border-radius: 5px;
    }

    .note {
      margin-top: 20px;
      font-size: 14px;
      color: #555;
    }

    .back-button {
      margin-top: 20px;
      padding: 8px 12px;
      background-color: #e74c3c;
      color: #fff;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }
        body {
            background: linear-gradient(45deg, blue, white);
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            overflow: hidden;
        }
        /* Container */
        .container {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(15px);
            padding: 20px;
            border-radius: 12px;
            box-shadow: 0px 4px 20px rgba(255, 255, 255, 0.3);
            width: 380px;
            text-align: center;
            animation: fadeIn 1s ease-in-out;
        }

        h2 {
            color: white;
            margin-bottom: 20px;
        }

        .payment-box {
            background: rgba(255, 255, 255, 0.2);
            padding: 15px;
            border-radius: 8px;
            margin: 10px 0;
            display: flex;
            justify-content: space-between;
            align-items: center;
            transition: 0.3s;
        }

        .payment-box:hover {
            transform: scale(1.05);
            box-shadow: 0 0 15px rgba(255, 255, 255, 0.5);
        }

        .payment-box img {
            width: 50px;
            border-radius: 5px;
        }

        .payment-info {
            color: white;
            flex-grow: 1;
            text-align: left;
            margin-left: 10px;
        }

        .copy-button, .qris-button {
            background: #ffdd57;
            color: black;
            font-weight: bold;
            border: none;
            padding: 8px 15px;
            border-radius: 5px;
            cursor: pointer;
            transition: 0.3s;
            position: relative;
            overflow: hidden;
        }

        .copy-button:hover, .qris-button:hover {
            background: #ffcc00;
            box-shadow: 0px 0px 10px rgba(255, 255, 255, 0.8);
        }

        /* Efek Gelembung */
        .copy-button::after {
            content: "";
            position: absolute;
            width: 150%;
            height: 150%;
            background: radial-gradient(circle, rgba(255, 255, 255, 0.3) 10%, transparent 50%);
            top: -50%;
            left: -50%;
            transform: scale(0);
            transition: transform 0.4s ease-out;
            border-radius: 50%;
        }

        .copy-button:active::after {
            transform: scale(1);
        }

        /* QRIS Button */
        .qris-button {
            background: #00e676;
            color: white;
            margin-top: 15px;
            width: 100%;
        }

        .qris-button:hover {
            background: #00c853;
        }

        /* Animasi */
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(-20px); }
            to { opacity: 1; transform: translateY(0); }
        }
  </style>
</head>
<body>
  <!-- Animasi loading -->
  <div id="loading">
    <div class="spinner"></div>
  </div>

  <!-- Konten utama -->

<div class="container">
    <h2>Pilih Salah Satu</h2>

    <div class="payment-box">
        <img src="https://files.catbox.moe/i1hcmu.jpg" alt="DANA">
        <div class="payment-info">
            <strong>DANA</strong>
            <p id="dana-number">083120589335</p>
        </div>
        <button class="copy-button" onclick="copyToClipboard('dana-number')">Salin</button>
    </div>

    <div class="payment-box">
        <img src="https://files.catbox.moe/c5qs0b.jpg" alt="OVO">
        <div class="payment-info">
            <strong>OVO</strong>
            <p id="ovo-number">087762544501</p>
        </div>
        <button class="copy-button" onclick="copyToClipboard('ovo-number')">Salin</button>
    </div>

    <div class="payment-box">
        <img src="https://files.catbox.moe/qbb1lk.jpg" alt="GoPay">
        <div class="payment-info">
            <strong>GoPay</strong>
            <p id="gopay-number">087762544501</p>
        </div>
        <button class="copy-button" onclick="copyToClipboard('gopay-number')">Salin</button>
    </div>

    <!-- Button QRIS -->
    <button class="qris-button" onclick="openQRIS()">Lihat QRIS</button>
</div>

<!-- Efek Suara -->
<audio id="bubbleSound" src="https://files.catbox.moe/od2x05.mp3" preload="auto"></audio>

  <script>
    // Tampilkan konten utama setelah 3 detik
    window.addEventListener('load', () => {
      setTimeout(() => {
        document.getElementById('loading').style.display = 'none';
        document.getElementById('main').style.display = 'flex';
      }, 3000);
    });

    // Fungsi untuk menyalin teks dan memutar suara
    function copyText(id) {
      const input = document.getElementById(id);
      input.select();
      input.setSelectionRange(0, 99999); // Untuk perangkat mobile
      document.execCommand('copy');

      // Putar suara
      const sound = document.getElementById('blub-sound');
      sound.currentTime = 0;
      sound.play();

      alert('Nomor berhasil disalin!');
    }

    // Fungsi untuk kembali ke halaman sebelumnya
    function goBack() {
      window.history.back();
    }
    function copyToClipboard(id) {
        let text = document.getElementById(id).innerText;
        let input = document.createElement("input");
        document.body.appendChild(input);
        input.value = text;
        input.select();
        document.execCommand("copy");
        document.body.removeChild(input);

        // Mainkan suara gelembung
        document.getElementById('bubbleSound').play();

        alert("Nomor berhasil disalin: " + text);
    }

    function openQRIS() {
        // Ganti dengan link gambar QRIS Anda
        let qrisLink = "https://files.catbox.moe/nlks1z.jpg"; 
        window.open(qrisLink, "_blank");
    }
  </script>
</body>
</html>
</body>
code>
