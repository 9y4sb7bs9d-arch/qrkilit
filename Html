<!DOCTYPE html>
<html lang="tr">
<head>
<meta charset="UTF-8">
<title>QR Kilit</title>

<script src="https://unpkg.com/html5-qrcode"></script>

<style>
body {
  font-family: Arial, Helvetica, sans-serif;
  text-align: center;
  margin-top: 30px;
}
#reader {
  width: 300px;
  margin: auto;
}
#sifre {
  font-size: 40px;
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
/* 🔐 Gizli anahtar */
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

  // DEBUG: Okunan QR'ı göster
  document.getElementById("sonuc").innerText =
    "Okunan QR: " + decodedText;

  // QR içeriği KESİN olarak bu olmalı
  if (decodedText.trim() !== "LOCK_QR_01") {
    document.getElementById("sifre").innerText = "";
    return;
  }

  if (localStorage.getItem("yetkili") !== "true") {
    document.getElementById("sonuc").innerText =
      "❌ Bu telefon yetkili değil";
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
