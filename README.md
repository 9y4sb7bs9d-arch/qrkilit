<!DOCTYPE html>
<html lang="tr">
<head>
<meta charset="UTF-8">
<title>QR Kilit</title>

<!-- QR okuma kütüphanesi -->
<script src="https://unpkg.com/html5-qrcode"></script>

<style>
body {
  font-family: Arial, Helvetica, sans-serif;
  text-align: center;
  margin-top: 40px;
  background: #f4f4f4;
}
h2 {
  color: #333;
}
button {
  font-size: 18px;
  padding: 10px 16px;
}
#reader {
  width: 300px;
  margin: auto;
}
#sifre {
  font-size: 42px;
  color: green;
  font-weight: bold;
}
</style>
</head>

<body>

<h2>QR Kilit Sistemi</h2>

<button onclick="yetkilendir()">Bu Cihazı Yetkilendir</button>
<br><br>

<div id="reader"></div>

<p id="sonuc"></p>
<div id="sifre"></div>

<script>
/* 🔐 Gizli anahtar (sadece sitede) */
const gizliAnahtar = 4321;

/* 📱 Telefonu yetkilendir */
function yetkilendir() {
  localStorage.setItem("yetkili", "true");
  alert("Bu telefon yetkilendirildi");
}

/* ⏱️ 30 saniyede bir değişen şifre */
function sifreUret() {
  const zaman = Math.floor(Date.now() / 1000 / 30);
  return (zaman + gizliAnahtar) % 10000;
}

/* 📷 QR okutulunca */
function onScanSuccess(decodedText) {
  if (decodedText !== "LOCK_QR_01") {
    document.getElementById("sonuc").innerText = "Yanlış QR kod";
    return;
  }

  if (localStorage.getItem("yetkili") !== "true") {
    document.getElementById("sonuc").innerText = "❌ Bu telefon yetkili değil";
    return;
  }

  const sifre = sifreUret();
  document.getElementById("sonuc").innerText =
    "✅ Şifre (30 saniye geçerli):";
  document.getElementById("sifre").innerText =
    sifre.toString().padStart(4, "0");
}

/* 📷 Kamerayı başlat */
new Html5Qrcode("reader").start(
  { facingMode: "environment" },
  { fps: 10, qrbox: 250 },
  onScanSuccess
);
</script>

</body>
</html>
