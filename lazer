<!DOCTYPE html>
<html lang="tr">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>İş Takip Uygulaması</title>
  <link
    href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;500;700&display=swap"
    rel="stylesheet"
  />
  <style>
    /* Genel Stil */
    body {
      font-family: 'Roboto', sans-serif;
      background: url('ata.jpg') no-repeat center center fixed;
      background-size: cover;
      margin: 0;
      padding: 0;
      color: #333;
      transition: background-color 0.5s, color 0.5s;
    }
    .night-mode {
      background: #000 url('ata.jpg') no-repeat center center fixed;
      background-size: cover;
      color: #fff;
    }
    .night-mode #app-section {
      background-color: rgba(0, 0, 0, 0.8);
      color: #fff;
    }
    .night-mode header,
    .night-mode footer {
      background-color: rgba(0, 0, 0, 0.8);
      color: #fff;
    }
    .night-mode .blinking-green {
      color: #0f0;
    }
    header {
      background-color: rgba(30, 42, 58, 0.8);
      color: #fff;
      text-align: center;
      padding: 20px;
      position: relative;
    }
    #logo {
      font-size: 24px;
      font-weight: bold;
      margin-bottom: 10px;
    }
    #login-buttons {
      margin-top: 10px;
    }
    #login-buttons button {
      padding: 10px 20px;
      margin: 0 5px;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      font-size: 14px;
      transition: background-color 0.3s;
    }
    #login-buttons button:hover {
      opacity: 0.9;
    }
    #google {
      background-color: #4285f4;
      color: #fff;
    }
    #tcmb-login {
      background-color: #34a853;
      color: #fff;
    }
    .blinking-green {
      color: green;
      font-weight: bold;
      animation: blink 1s infinite;
    }
    @keyframes blink {
      0% { opacity: 1; }
      50% { opacity: 0.5; }
      100% { opacity: 1; }
    }
    #app-section {
      padding: 20px;
      max-width: 1200px;
      margin: 0 auto;
      background-color: rgba(255, 255, 255, 0.8);
      border-radius: 10px;
      transition: background-color 0.5s, color 0.5s;
    }
    input, select, button {
      width: 100%;
      padding: 10px;
      margin: 10px 0;
      box-sizing: border-box;
      border: 1px solid #ccc;
      border-radius: 5px;
    }
    button {
      background-color: #007bff;
      color: #fff;
      border: none;
      cursor: pointer;
      transition: background-color 0.3s;
    }
    button:hover {
      background-color: #0056b3;
    }
    h3, h4, p, label {
      font-weight: 600;
    }
    /* Arama Filtreleri */
    #search-filters {
      margin-bottom: 20px;
    }
    #search-filters label {
      display: inline-block;
      margin-right: 5px;
    }
    #search-filters input {
      margin-right: 15px;
      max-width: 200px;
    }
    /* Firma Listesi (dikey kaydırma) */
    #firm-list {
      list-style: none;
      padding: 0;
      max-height: 200px;   /* Maksimum yükseklik */
      overflow-y: auto;    /* Dikey kaydırma */
    }
    #firm-list li {
      background-color: #fff;
      padding: 10px;
      margin-bottom: 10px;
      border: 1px solid #ddd;
      border-radius: 5px;
      transition: background-color 0.3s;
    }
    #firm-list li:hover {
      background-color: #f9f9f9;
    }
    .firm-link {
      color: blue;
      font-weight: bold;
      text-decoration: none;
      cursor: pointer;
    }
    /* Tablo Stilleri */
    table {
      width: 100%;
      border-collapse: collapse;
      margin-top: 20px;
    }
    table, th, td {
      border: 1px solid #ddd;
    }
    th, td {
      padding: 12px;
      text-align: center;
    }
    th {
      background-color: #f1f1f1;
    }
    .edit-btn, .delete-btn {
      padding: 5px 10px;
      margin: 0 5px;
      border-radius: 3px;
      cursor: pointer;
    }
    .edit-btn {
      background-color: #ffc107;
      color: #000;
    }
    .delete-btn {
      background-color: #dc3545;
      color: #fff;
    }
    #clear-btn {
      background-color: #dc3545;
    }
    #clear-btn:hover {
      background-color: #c82333;
    }
    footer {
      background-color: rgba(30, 42, 58, 0.8);
      color: #fff;
      text-align: center;
      padding: 20px;
      margin-top: 40px;
    }
    footer a {
      color: #fff;
      text-decoration: none;
      margin: 0 10px;
    }
    footer a:hover {
      text-decoration: underline;
    }
    /* Toast Mesajı */
    .toast {
      position: fixed;
      top: 20px;
      right: 20px;
      background-color: rgba(255,255,255,0.9);
      color: #28a745;
      padding: 20px 40px;
      border-radius: 8px;
      font-size: 24px;
      font-weight: bold;
      z-index: 10000;
      opacity: 0;
      pointer-events: none;
      transition: opacity 0.5s ease-in-out;
    }
    /* Loader */
    .loader {
      position: fixed;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      border: 4px solid #f3f3f3;
      border-top: 4px solid #007bff;
      border-radius: 50%;
      width: 40px;
      height: 40px;
      animation: spin 1s linear infinite;
      display: none;
      z-index: 1000;
    }
    @keyframes spin {
      0% { transform: translate(-50%, -50%) rotate(0deg); }
      100% { transform: translate(-50%, -50%) rotate(360deg); }
    }
    /* Modal */
    #company-details-modal,
    #job-details-modal {
      position: fixed;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      background: #fff;
      border: 2px solid #007bff;
      border-radius: 8px;
      padding: 20px;
      z-index: 2000;
      display: none;
      max-width: 90%;
      max-height: 90%;
      overflow: auto;
    }
    #company-details-modal h3,
    #job-details-modal h3 {
      margin-top: 0;
    }
    #company-details-modal .close-btn,
    #job-details-modal .close-btn {
      position: absolute;
      top: 10px;
      right: 10px;
      background-color: #dc3545;
      color: #fff;
      border: none;
      padding: 5px 10px;
      cursor: pointer;
    }
    .night-mode #company-details-modal,
    .night-mode #job-details-modal {
      background: #333;
      color: #fff;
      border-color: #fff;
    }
    .night-mode #company-details-modal table th,
    .night-mode #job-details-modal table th {
      background-color: #444;
      color: #fff;
    }
    .night-mode #company-details-modal table td,
    .night-mode #job-details-modal table td {
      background-color: #333;
      color: #fff;
    }
    /* Firma Son Veri Girişi (dikey kaydırma) */
    #company-last-entry-container {
      max-height: 300px;
      overflow-y: auto;
    }
    #company-last-entry table {
      width: 100%;
      border-collapse: collapse;
    }
    #company-last-entry th,
    #company-last-entry td {
      padding: 10px;
      border: 1px solid #ddd;
      text-align: center;
    }
    #company-last-entry th {
      background-color: #f1f1f1;
    }
    .night-mode #company-last-entry th {
      background-color: #444;
      color: #fff;
    }
    .night-mode #company-last-entry td {
      background-color: #333;
      color: #fff;
    }
    /* Gündüz/Gece Modu Butonu */
    #mode-toggle-btn {
      position: absolute;
      top: 20px;
      right: 20px;
      width: 40px;
      height: 40px;
      background-color: #ff9800;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      transition: background-color 0.3s;
      outline: none;
    }
    #mode-toggle-btn::before {
      content: "☀";
      display: block;
      font-size: 20px;
      line-height: 38px;
      text-align: center;
      color: #fff;
    }
    .night-mode #mode-toggle-btn {
      background-color: #444;
    }
    .night-mode #mode-toggle-btn::before {
      content: "🌙";
    }
    #mode-toggle-btn:hover {
      background-color: #e68a00;
    }
    .night-mode #mode-toggle-btn:hover {
      background-color: #555;
    }
    /* Checkbox */
    .checkbox-container {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      margin: 10px 0;
    }
    .checkbox-container label {
      position: relative;
      cursor: pointer;
      user-select: none;
      padding-left: 30px;
    }
    .checkbox-container input[type="checkbox"] {
      position: absolute;
      opacity: 0;
      cursor: pointer;
      height: 0;
      width: 0;
    }
    .checkmark {
      position: absolute;
      left: 0;
      top: 3px;
      height: 20px;
      width: 20px;
      background-color: #fff;
      border: 2px solid #ccc;
      border-radius: 4px;
      transition: 0.3s;
    }
    .checkbox-container input[type="checkbox"]:checked ~ .checkmark {
      background-color: green;
      border-color: green;
    }
    .checkbox-container .checkmark:after {
      content: "";
      position: absolute;
      display: none;
    }
    .checkbox-container input[type="checkbox"]:checked ~ .checkmark:after {
      display: block;
    }
    .checkbox-container .checkmark:after {
      left: 6px;
      top: 2px;
      width: 5px;
      height: 10px;
      border: solid #fff;
      border-width: 0 3px 3px 0;
      transform: rotate(45deg);
    }
    /* Toplam Tutarlar */
    #total-amounts {
      background: #f1f1f1;
      padding: 10px;
      border-radius: 5px;
      margin-top: 20px;
    }
    /* Dışa Aktarma Butonu */
    #export-button {
      background-color: transparent;
      border: 2px solid green;
      border-radius: 5px;
      padding: 10px;
      cursor: pointer;
      margin-bottom: 10px;
    }
    .blink-text {
      animation: blink 1s infinite;
      color: green;
      font-weight: bold;
    }
    /* Onay Modalı */
    #confirmation-modal {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      display: none;
      align-items: center;
      justify-content: center;
      background: rgba(0, 0, 0, 0.5);
      z-index: 3000;
    }
    #confirmation-modal .modal-content {
      background: #fff;
      padding: 20px;
      border-radius: 8px;
      text-align: center;
    }
    #confirmation-message {
      font-size: 18px;
      font-weight: bold;
      margin-bottom: 20px;
    }
    #confirm-yes {
      background-color: green;
      color: #fff;
      border: none;
      padding: 10px 20px;
      border-radius: 5px;
      margin: 5px;
      cursor: pointer;
    }
    #confirm-no {
      background-color: red;
      color: #fff;
      border: none;
      padding: 10px 20px;
      border-radius: 5px;
      margin: 5px;
      cursor: pointer;
    }
    /* Grafik Kapsayıcısı (yatay kaydırma) */
    #firm-performance-container {
      overflow-x: auto;
    }
    /* Grafiğin min. genişliği */
    #firm-performance-chart {
      min-width: 600px;
    }
    /* Her firmanın toplam verilerini gösteren kutucuklar (yeşil yazı) */
    .currency-totals {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 10px;
      margin-top: 10px;
    }
    .currency-box {
      background-color: #f9f9f9;
      border: 1px solid #ccc;
      padding: 10px;
      border-radius: 5px;
      min-width: 100px;
      text-align: center;
      font-size: 14px;
      color: green;
      font-weight: bold;
    }
    /* Yapılan İşler Tablosu için dikey kaydırma */
    #work-table-container {
      max-height: 300px;
      overflow-y: auto;
      margin-top: 10px;
    }
    /* Yıldızın yanıp sönmesi (daha belirgin) */
    .star-blink {
      display: inline-block;
      font-size: 20px;     /* Daha büyük */
      color: gold;
      margin-left: 4px;
      animation: starBlink 0.5s infinite alternate;
    }
    @keyframes starBlink {
      from { transform: scale(1);   }
      to   { transform: scale(1.6); }
    }
  </style>
</head>
<body>
  <header>
    <div id="logo">İstanbul Teknik Lazer Gökberk</div>
    <div id="login-buttons">
      <button id="google" onclick="window.open('https://google.com', '_blank')">Google Giriş</button>
      <button id="tcmb-login" onclick="window.open('https://www.tcmb.gov.tr', '_blank')">TCMB Giriş</button>
    </div>
    <div class="blinking-green">Son Veri Girişi</div>
    <button id="mode-toggle-btn" onclick="toggleMode()"></button>
  </header>

  <div id="app-section">
    <!-- Veri Girişi Formu -->
    <h3>Veri Girişi</h3>
    <input type="text" id="firm-name" placeholder="Firma İsmi" />
    <input type="text" id="work-description" placeholder="Yapılan İş Açıklaması" />
    <input type="number" id="amount" placeholder="Fiyat" step="0.01" />
    <select id="currency">
      <option value="TL">TL</option>
      <option value="USD">USD</option>
      <option value="EUR">EUR</option>
    </select>
    <input type="text" id="program-name" placeholder="Program İsmi" />

    <!-- İşlem Kutucukları -->
    <div class="checkbox-container">
      <label>
        <input type="checkbox" name="islem" value="lazer" />
        <span class="checkmark"></span> Lazer Kesim
      </label>
      <label>
        <input type="checkbox" name="islem" value="bukum" />
        <span class="checkmark"></span> Büküm
      </label>
      <label>
        <input type="checkbox" name="islem" value="kaynak" />
        <span class="checkmark"></span> Kaynak
      </label>
      <label>
        <input type="checkbox" name="islem" value="makas" />
        <span class="checkmark"></span> Makas
      </label>
    </div>

    <button id="submit-button" onclick="addData()">Veri Girişi</button>
    <button id="clear-btn" onclick="verifyPIN()">Verileri Temizle</button>
    <button id="export-button" onclick="exportToCSV()">
      <span class="blink-text">Verileri Dışarı Aktar Kaydet</span>
    </button>
    <input
      type="file"
      id="csv-file-input"
      accept=".csv"
      style="display: none;"
      onchange="importCSV(event)"
    />
    <button onclick="document.getElementById('csv-file-input').click()">
      Verileri CSV Olarak Yükle
    </button>

    <!-- Firma Listesi (dikey kaydırmalı) -->
    <h3>Firma Listesi</h3>
    <ul id="firm-list"></ul>

    <!-- Arama Filtreleri -->
    <div id="search-filters">
      <label>Başlangıç Tarihi:</label>
      <input type="date" id="search-start-date" onchange="filterTable()" />
      <label>Bitiş Tarihi:</label>
      <input type="date" id="search-end-date" onchange="filterTable()" />
      <label>Program Adı:</label>
      <input
        type="text"
        id="search-program"
        oninput="filterTable()"
        placeholder="Program adı girin..."
      />
    </div>

    <!-- Yapılan İşler Tablosu (dikey kaydırma) -->
    <h3>Yapılan İşler</h3>
    <div>
      <label for="filter-firm">Firma Filtrele:</label>
      <input
        type="text"
        id="filter-firm"
        oninput="filterTable()"
        placeholder="Firma adı girin..."
      />
      <label for="sort-by">Sırala:</label>
      <select id="sort-by" onchange="sortTable()">
        <option value="date">Tarihe Göre</option>
        <option value="firm">Firmaya Göre</option>
        <option value="program">Programa Göre</option>
      </select>
    </div>
    <div id="work-table-container">
      <table>
        <thead>
          <tr>
            <th>Tarih</th>
            <th>Yapılan İş</th>
            <th>Firma</th>
            <th>Fiyat</th>
            <th>Firma Toplam</th>
            <th>Program</th>
            <th>Muhasebeye Verildi</th>
            <th>İşlemler</th>
          </tr>
        </thead>
        <tbody id="work-table-body"></tbody>
      </table>
    </div>

    <!-- Firmaların Son Veri Girişi (dikey kaydırma) -->
    <h3>Firmaların Son Veri Girişi</h3>
    <div id="company-last-entry-container">
      <div id="company-last-entry"></div>
    </div>

    <!-- Toplam Tutarlar -->
    <div id="total-amounts">
      <h3>Toplam Tutarlar</h3>
      <p style="color: green;">USD: <span id="total-usd">0</span></p>
      <p style="color: green;">TL: <span id="total-tl">0</span></p>
      <p style="color: green;">EUR: <span id="total-eur">0</span></p>
    </div>

    <!-- Firmalara Göre İş Performansı Grafiği ve Firma Bazında Toplamlar -->
    <h3>Firmalara Göre İş Performansı</h3>
    <div id="firm-performance-container">
      <canvas id="firm-performance-chart"></canvas>
    </div>
    <!-- Her firmanın toplam verilerini gösteren küçük kutucuklar (yeşil renk) -->
    <div id="currency-totals" class="currency-totals"></div>
  </div>

  <footer>
    <p>© 2023 İstanbul Teknik Lazer Gökberk. Tüm hakları saklıdır.</p>
    <p>
      <a href="#">Gizlilik Politikası</a> |
      <a href="#">Kullanım Koşulları</a> |
      <a href="#">İletişim</a>
    </p>
  </footer>

  <!-- Toast -->
  <div id="toast" class="toast"></div>

  <!-- Loader -->
  <div id="loader" class="loader"></div>

  <!-- Firma Detayları Modalı -->
  <div id="company-details-modal">
    <button class="close-btn" onclick="closeCompanyDetails()">X</button>
    <div id="company-details-content"></div>
  </div>

  <!-- İş Detayları Modalı -->
  <div id="job-details-modal">
    <button class="close-btn" onclick="closeJobDetails()">X</button>
    <div id="job-details-content"></div>
  </div>

  <!-- Onay Modalı -->
  <div id="confirmation-modal">
    <div class="modal-content">
      <p id="confirmation-message">Emin misiniz?</p>
      <button id="confirm-yes">Onayla</button>
      <button id="confirm-no">İptal</button>
    </div>
  </div>

  <script>
    /*********************************************************
     *  1) Global Değişkenler ve Kur Ayarları
     *********************************************************/
    let editingIndex = null;
    let entries = JSON.parse(localStorage.getItem('entries')) || [];
    let pendingAction = null;
    let pendingIndex = null;

    // Basit bir kur seti (1 TL, 27 TL = 1 USD, 29 TL = 1 EUR gibi)
    const conversionRates = {
      TL: 1,
      USD: 27,
      EUR: 29
    };

    /*********************************************************
     *  2) Gündüz/Gece Modu
     *********************************************************/
    function toggleMode() {
      document.body.classList.toggle('night-mode');
    }

    /*********************************************************
     *  3) Tarih Formatlama
     *********************************************************/
    function formatDate() {
      const date = new Date();
      const day = String(date.getDate()).padStart(2, '0');
      const month = String(date.getMonth() + 1).padStart(2, '0');
      const year = date.getFullYear();
      return `${day}.${month}.${year}`;
    }

    function parseDate(dateStr) {
      const parts = dateStr.split('.');
      return new Date(parts[2], parts[1] - 1, parts[0]);
    }

    /*********************************************************
     *  4) Toast Mesajı
     *********************************************************/
    function showToast(message) {
      const toast = document.getElementById('toast');
      toast.textContent = message;
      toast.style.animation = 'none';
      void toast.offsetWidth;
      toast.style.animation = '';
      toast.style.opacity = 1;
      setTimeout(() => {
        toast.style.opacity = 0;
      }, 3000);
    }

    /*********************************************************
     *  5) Loader Göster/Gizle
     *********************************************************/
    function showLoader(show) {
      document.getElementById('loader').style.display = show ? 'block' : 'none';
    }

    /*********************************************************
     *  6) Firma Toplamlarını Güncelleme
     *********************************************************/
    function updateFirmTotals(firmName, amount, currency) {
      let firmTotals = JSON.parse(localStorage.getItem('firmTotals')) || {};
      const key = `${firmName}-${currency}`;
      firmTotals[key] = (firmTotals[key] || 0) + amount;
      localStorage.setItem('firmTotals', JSON.stringify(firmTotals));
    }

    /*********************************************************
     *  7) Firmanın Toplam Parasal Değerini Hesaplama
     *********************************************************/
    function calcFirmValue(firmName) {
      // Bu firmaya ait tüm entries'leri bulup, TL cinsinden toplamını döndürür.
      let totalValue = 0;
      entries.forEach(entry => {
        if (entry.firmName === firmName) {
          // conversionRates ile TL'ye çeviriyoruz
          const rate = conversionRates[entry.currency] || 1;
          totalValue += (entry.amount * rate);
        }
      });
      return totalValue;
    }

    /*********************************************************
     *  8) Belirli firmaya ait (TL, USD, EUR) toplamlari
     *********************************************************/
    function getFirmTotals(firmName) {
      let totals = { TL: 0, USD: 0, EUR: 0 };
      entries.forEach(entry => {
        if (entry.firmName === firmName) {
          totals[entry.currency] += entry.amount;
        }
      });
      return totals;
    }

    /*********************************************************
     *  9) Toplam Tutarları Güncelle (genel)
     *********************************************************/
    function updateTotalAmounts() {
      let totalUSD = 0, totalTL = 0, totalEUR = 0;
      entries.forEach(entry => {
        if (entry.currency === 'USD') totalUSD += entry.amount;
        else if (entry.currency === 'TL') totalTL += entry.amount;
        else if (entry.currency === 'EUR') totalEUR += entry.amount;
      });
      document.getElementById('total-usd').textContent = totalUSD.toFixed(2);
      document.getElementById('total-tl').textContent = totalTL.toFixed(2);
      document.getElementById('total-eur').textContent = totalEUR.toFixed(2);
    }

    /*********************************************************
     * 10) Veri Girişi (Ekle/Düzenle)
     *********************************************************/
    function addData() {
      const firmName = document.getElementById('firm-name').value.trim();
      const description = document.getElementById('work-description').value.trim();
      const amount = parseFloat(document.getElementById('amount').value);
      const currency = document.getElementById('currency').value;
      const programName = document.getElementById('program-name').value.trim();
      const checkboxes = document.querySelectorAll('input[name="islem"]');
      const selectedIslem = [];
      checkboxes.forEach(cb => { if (cb.checked) selectedIslem.push(cb.value); });

      if (!firmName || !description || isNaN(amount) || amount <= 0 || !programName) {
        alert('Lütfen tüm alanları geçerli şekilde doldurun.');
        return;
      }

      // Aynı program koduna izin verilmiyor
      if (editingIndex === null) {
        if (entries.some(entry => entry.programName.toLowerCase() === programName.toLowerCase())) {
          alert("Aynı program koduna izin verilmiyor.");
          return;
        }
      } else {
        if (entries.some((entry, idx) => idx !== editingIndex && entry.programName.toLowerCase() === programName.toLowerCase())) {
          alert("Aynı program koduna izin verilmiyor.");
          return;
        }
      }

      showLoader(true);
      setTimeout(() => {
        if (editingIndex !== null) {
          // Düzenleme
          const oldEntry = entries[editingIndex];
          updateFirmTotals(oldEntry.firmName, -oldEntry.amount, oldEntry.currency);
          entries[editingIndex] = {
            date: formatDate(),
            firmName,
            description,
            amount,
            currency,
            programName,
            islem: selectedIslem,
            muhasebeyeVerildi: oldEntry.muhasebeyeVerildi || false
          };
          updateFirmTotals(firmName, amount, currency);
          showToast('Veri güncellendi!');
          editingIndex = null;
          document.getElementById('submit-button').textContent = 'Veri Girişi';
        } else {
          // Yeni Ekleme
          entries.push({
            date: formatDate(),
            firmName,
            description,
            amount,
            currency,
            programName,
            islem: selectedIslem,
            muhasebeyeVerildi: false
          });
          updateFirmTotals(firmName, amount, currency);
          showToast('Başarıyla eklendi!');
        }
        localStorage.setItem('entries', JSON.stringify(entries));
        loadEntries();
        loadFirms();
        loadCompanyLastEntry();
        updateTotalAmounts();
        clearForm();
        showLoader(false);
        renderFirmPerformanceChart();
      }, 1000);
    }

    /*********************************************************
     * 11) Kayıt Silme
     *********************************************************/
    function deleteEntry(index) {
      const entry = entries[index];
      entries.splice(index, 1);
      localStorage.setItem('entries', JSON.stringify(entries));
      updateFirmTotals(entry.firmName, -entry.amount, entry.currency);
      loadEntries();
      loadFirms();
      loadCompanyLastEntry();
      updateTotalAmounts();
      showToast('Kayıt silindi!');
      renderFirmPerformanceChart();
    }

    /*********************************************************
     * 12) Kayıt Düzenleme
     *********************************************************/
    function editEntry(index) {
      editingIndex = index;
      const entry = entries[index];
      document.getElementById('firm-name').value = entry.firmName;
      document.getElementById('work-description').value = entry.description;
      document.getElementById('amount').value = entry.amount;
      document.getElementById('currency').value = entry.currency;
      document.getElementById('program-name').value = entry.programName;
      const checkboxes = document.querySelectorAll('input[name="islem"]');
      checkboxes.forEach(cb => { cb.checked = entry.islem && entry.islem.includes(cb.value); });
      document.getElementById('submit-button').textContent = 'Güncelle';
    }

    /*********************************************************
     * 13) Form Temizleme
     *********************************************************/
    function clearForm() {
      document.getElementById('firm-name').value = '';
      document.getElementById('work-description').value = '';
      document.getElementById('amount').value = '';
      document.getElementById('program-name').value = '';
      const checkboxes = document.querySelectorAll('input[name="islem"]');
      checkboxes.forEach(cb => { cb.checked = false; });
      document.getElementById('submit-button').textContent = 'Veri Girişi';
    }

    /*********************************************************
     * 14) Tabloya Kayıtları Yükleme
     *********************************************************/
    let topFirmNames = []; // En çok iş veren firmaların adlarını burada tutacağız

    function loadEntries(filteredData = entries) {
      const tableBody = document.getElementById('work-table-body');
      tableBody.innerHTML = '';
      filteredData.forEach((entry, index) => {
        const row = tableBody.insertRow();
        const dateCell = row.insertCell();
        const descCell = row.insertCell();
        const firmCell = row.insertCell();
        const amountCell = row.insertCell();
        const firmTotalCell = row.insertCell();
        const programCell = row.insertCell();
        const muhCell = row.insertCell();
        const actionsCell = row.insertCell();

        // Tarih
        dateCell.textContent = entry.date;

        // Açıklama + kutucuklar
        let islemText = '';
        if (entry.islem && entry.islem.length > 0) {
          islemText = ` (Seçilen: ${entry.islem.join(', ')})`;
        }
        descCell.textContent = entry.description + islemText;
        descCell.style.cursor = 'pointer';
        descCell.onclick = () => showJobDetails(entry);

        // Firma (yıldız ekleyecek miyiz?)
        let starHTML = '';
        if (topFirmNames.includes(entry.firmName)) {
          starHTML = '<span class="star-blink">★</span>';
        }
        firmCell.innerHTML = `
          <span class="firm-link" style="cursor:pointer;" onclick="showCompanyDetails('${entry.firmName}')">
            ${entry.firmName}${starHTML}
          </span>
        `;

        // Fiyat
        amountCell.textContent = `${entry.amount} ${entry.currency}`;
        amountCell.style.color = 'green';

        // Firma Toplam
        const totals = getFirmTotals(entry.firmName);
        firmTotalCell.innerHTML = `<div style="color: green; font-weight: bold;">
          TL: ${totals.TL.toFixed(2)}<br>
          USD: ${totals.USD.toFixed(2)}<br>
          EUR: ${totals.EUR.toFixed(2)}
        </div>`;

        // Program
        programCell.textContent = entry.programName;

        // Muhasebeye Verildi
        const muhCheckbox = document.createElement('input');
        muhCheckbox.type = 'checkbox';
        muhCheckbox.checked = entry.muhasebeyeVerildi === true;
        muhCheckbox.addEventListener('change', function () {
          entry.muhasebeyeVerildi = muhCheckbox.checked;
          localStorage.setItem('entries', JSON.stringify(entries));
          updateMuhCell(muhCell, entry);
        });
        updateMuhCell(muhCell, entry);

        // İşlemler (Düzenle/Sil)
        const editBtn = document.createElement('button');
        editBtn.textContent = 'Düzenle';
        editBtn.className = 'edit-btn';
        editBtn.onclick = () => openConfirmation('edit', index);

        const deleteBtn = document.createElement('button');
        deleteBtn.textContent = 'Sil';
        deleteBtn.className = 'delete-btn';
        deleteBtn.onclick = () => openConfirmation('delete', index);

        actionsCell.appendChild(editBtn);
        actionsCell.appendChild(deleteBtn);
      });
    }

    function updateMuhCell(cell, entry) {
      if (entry.muhasebeyeVerildi) {
        cell.innerHTML = "<span style='color:green; font-weight:bold;'>Fatura Edildi &#10003;</span>";
      } else {
        cell.innerHTML = "";
        const checkbox = document.createElement('input');
        checkbox.type = 'checkbox';
        checkbox.checked = false;
        checkbox.addEventListener('change', function() {
          entry.muhasebeyeVerildi = checkbox.checked;
          localStorage.setItem('entries', JSON.stringify(entries));
          updateMuhCell(cell, entry);
        });
        cell.appendChild(checkbox);
      }
    }

    /*********************************************************
     * 15) Firma Listesi
     *********************************************************/
    function loadFirms() {
      const firmListEl = document.getElementById('firm-list');
      firmListEl.innerHTML = '';
      const firms = getUniqueFirms();
      firms.forEach(firm => {
        const li = document.createElement('li');
        const a = document.createElement('a');
        a.textContent = firm;
        a.href = "javascript:void(0)"; // Tıklayınca sayfa kaymasın
        a.classList.add('firm-link');
        a.onclick = () => showCompanyDetails(firm);
        li.appendChild(a);
        firmListEl.appendChild(li);
      });
    }

    function getUniqueFirms() {
      const firms = new Set();
      entries.forEach(entry => {
        firms.add(entry.firmName);
      });
      return Array.from(firms);
    }

    /*********************************************************
     * 16) Filtreleme
     *********************************************************/
    function filterTable() {
      const firmFilterText = document.getElementById('filter-firm').value.toLowerCase();
      const searchStartDate = document.getElementById('search-start-date').value;
      const searchEndDate = document.getElementById('search-end-date').value;
      const searchProgram = document.getElementById('search-program').value.toLowerCase();

      const filtered = entries.filter(entry => {
        if (firmFilterText && !entry.firmName.toLowerCase().includes(firmFilterText))
          return false;
        const entryDate = parseDate(entry.date);
        if (searchStartDate) {
          const startDate = new Date(searchStartDate);
          if (entryDate < startDate) return false;
        }
        if (searchEndDate) {
          const endDate = new Date(searchEndDate);
          if (entryDate > endDate) return false;
        }
        if (searchProgram && !entry.programName.toLowerCase().includes(searchProgram))
          return false;
        return true;
      });
      loadEntries(filtered);
    }

    /*********************************************************
     * 17) Sıralama
     *********************************************************/
    function sortTable() {
      const sortBy = document.getElementById('sort-by').value;
      entries.sort((a, b) => {
        if (sortBy === 'date') {
          // Tarihe göre sırala
          const dateA = new Date(a.date.split('.').reverse().join('-'));
          const dateB = new Date(b.date.split('.').reverse().join('-'));
          return dateA - dateB;
        } else if (sortBy === 'firm') {
          // Firma adına göre
          return a.firmName.localeCompare(b.firmName);
        } else if (sortBy === 'program') {
          // Programa göre
          return a.programName.localeCompare(b.programName);
        }
      });
      localStorage.setItem('entries', JSON.stringify(entries));
      loadEntries();
    }

    /*********************************************************
     * 18) CSV Dışa Aktarma
     *********************************************************/
    function exportToCSV() {
      if (entries.length === 0) {
        alert('Dışa aktarılacak veri yok.');
        return;
      }
      let csvContent = 'data:text/csv;charset=utf-8,';
      csvContent += `"Tarih","Yapılan İş","Firma","Fiyat","Para Birimi","Program","Muhasebeye Verildi","Seçilen İşlemler"\n`;
      entries.forEach(entry => {
        const islemList = entry.islem ? entry.islem.join('|') : '';
        const muh = entry.muhasebeyeVerildi ? 'Fatura Edildi' : '';
        const row = [
          entry.date,
          entry.description,
          entry.firmName,
          entry.amount,
          entry.currency,
          entry.programName,
          muh,
          islemList
        ];
        csvContent += row.map(field => `"${field}"`).join(',') + '\n';
      });
      const encodedUri = encodeURI(csvContent);
      const link = document.createElement('a');
      link.setAttribute('href', encodedUri);
      link.setAttribute('download', 'veriler.csv');
      document.body.appendChild(link);
      link.click();
      document.body.removeChild(link);
    }

    /*********************************************************
     * 19) CSV Parser ve Yükleme
     *********************************************************/
    function parseCSVLine(line) {
      const result = [];
      let curVal = "";
      let inQuotes = false;
      for (let i = 0; i < line.length; i++) {
        const char = line[i];
        if (inQuotes) {
          if (char === '"') {
            if (i + 1 < line.length && line[i + 1] === '"') {
              curVal += '"';
              i++;
            } else {
              inQuotes = false;
            }
          } else {
            curVal += char;
          }
        } else {
          if (char === '"') {
            inQuotes = true;
          } else if (char === ',') {
            result.push(curVal);
            curVal = "";
          } else {
            curVal += char;
          }
        }
      }
      result.push(curVal);
      return result;
    }

    function importCSV(event) {
      const file = event.target.files[0];
      if (!file) return;
      const reader = new FileReader();
      reader.onload = function(e) {
        const text = e.target.result;
        const lines = text.trim().split('\n');
        const newEntries = [];
        for (let i = 1; i < lines.length; i++) {
          const cols = parseCSVLine(lines[i]);
          if (cols.length < 8) continue;
          const [date, description, firmName, amount, currency, programName, muh, islemList] = cols;
          const parsedIslem = islemList ? islemList.split('|') : [];
          newEntries.push({
            date: date.trim(),
            description: description.trim(),
            firmName: firmName.trim(),
            amount: parseFloat(amount),
            currency: currency.trim(),
            programName: programName.trim(),
            islem: parsedIslem,
            muhasebeyeVerildi: muh.trim().toLowerCase() === 'fatura edildi'
          });
        }
        entries = newEntries;
        localStorage.setItem('entries', JSON.stringify(entries));
        loadEntries();
        loadFirms();
        loadCompanyLastEntry();
        updateTotalAmounts();
        showToast('CSV başarıyla yüklendi!');
        renderFirmPerformanceChart();
      };
      reader.readAsText(file);
    }

    /*********************************************************
     * 20) Verileri Temizleme (PIN Doğrulaması)
     *********************************************************/
    function verifyPIN() {
      const pin = prompt('Verileri temizlemek için PIN giriniz:');
      if (pin === '1234') {
        entries = [];
        localStorage.removeItem('entries');
        localStorage.removeItem('firmTotals');
        loadEntries();
        loadFirms();
        loadCompanyLastEntry();
        updateTotalAmounts();
        showToast('Veriler temizlendi!');
        renderFirmPerformanceChart();
      } else {
        alert('Yanlış PIN!');
      }
    }

    /*********************************************************
     * 21) Firma Son Giriş Tarihi
     *********************************************************/
    function getLatestEntryDate(firmName) {
      let latest = null;
      entries.forEach(entry => {
        if (entry.firmName === firmName) {
          const entryDate = parseDate(entry.date);
          if (!latest || entryDate > latest) latest = entryDate;
        }
      });
      return latest;
    }

    /*********************************************************
     * 22) Firmaların Son Veri Girişi
     *********************************************************/
    function loadCompanyLastEntry() {
      const container = document.getElementById('company-last-entry');
      container.innerHTML = '';
      const firms = getUniqueFirms();
      if (firms.length === 0) {
        container.innerHTML = '<p>Henüz firma verisi yok.</p>';
        return;
      }
      const table = document.createElement('table');
      const thead = document.createElement('thead');
      const headerRow = document.createElement('tr');
      const thFirm = document.createElement('th');
      thFirm.textContent = 'Firma';
      const thLastEntry = document.createElement('th');
      thLastEntry.textContent = 'Son Veri Girişi';
      headerRow.appendChild(thFirm);
      headerRow.appendChild(thLastEntry);
      thead.appendChild(headerRow);
      table.appendChild(thead);
      const tbody = document.createElement('tbody');
      firms.forEach(firm => {
        const tr = document.createElement('tr');
        const tdFirm = document.createElement('td');
        const firmLink = document.createElement('a');
        firmLink.textContent = firm;
        firmLink.href = "javascript:void(0)";
        firmLink.classList.add('firm-link');
        firmLink.onclick = () => showCompanyDetails(firm);
        tdFirm.appendChild(firmLink);
        const tdLastEntry = document.createElement('td');
        const latestDate = getLatestEntryDate(firm);
        tdLastEntry.textContent = latestDate ? latestDate.toLocaleDateString('tr-TR') : 'Yok';
        tr.appendChild(tdFirm);
        tr.appendChild(tdLastEntry);
        tbody.appendChild(tr);
      });
      table.appendChild(tbody);
      container.appendChild(table);
    }

    /*********************************************************
     * 23) Firma Detayları Modalı
     *********************************************************/
    function showCompanyDetails(firmName) {
      const firmEntries = entries.filter(entry => entry.firmName === firmName);
      if (firmEntries.length === 0) return;
      let totalTL = 0, totalUSD = 0, totalEUR = 0;
      firmEntries.forEach(entry => {
        if (entry.currency === 'TL') totalTL += entry.amount;
        else if (entry.currency === 'USD') totalUSD += entry.amount;
        else if (entry.currency === 'EUR') totalEUR += entry.amount;
      });
      const latestDate = getLatestEntryDate(firmName);
      const latestDateStr = latestDate ? latestDate.toLocaleDateString('tr-TR') : 'Yok';
      const monthlyData = {};
      firmEntries.forEach(entry => {
        const date = parseDate(entry.date);
        const monthYear = `${date.getFullYear()}-${(date.getMonth() + 1).toString().padStart(2, '0')}`;
        if (!monthlyData[monthYear]) monthlyData[monthYear] = 0;
        monthlyData[monthYear]++;
      });
      const modalContent = document.getElementById('company-details-content');
      modalContent.innerHTML = `<h3>${firmName} Detayları</h3>
        <p><strong>Toplam İş Tutarı:</strong></p>
        <div style="color: green; font-weight: bold; border: 1px solid #ccc; padding: 5px; border-radius: 5px;">
          TL: ${totalTL.toFixed(2)}<br>
          USD: ${totalUSD.toFixed(2)}<br>
          EUR: ${totalEUR.toFixed(2)}
        </div>
        <p><strong>Son Veri Girişi:</strong> ${latestDateStr}</p>
        <p><strong>Veri Girişi Yapılmadığı Süre:</strong> ${
          latestDate
            ? Math.floor((new Date() - latestDate) / (1000 * 60 * 60 * 24))
            : '0'
        } gün</p>
        <h4>Aylara Göre Veri Girişi</h4>
        <table>
          <thead>
            <tr>
              <th>Ay</th>
              <th>Giriş Sayısı</th>
            </tr>
          </thead>
          <tbody>
            ${Object.entries(monthlyData)
              .map(([month, count]) => `<tr><td>${month}</td><td>${count}</td></tr>`)
              .join('')}
          </tbody>
        </table>`;
      document.getElementById('company-details-modal').style.display = 'block';
    }

    function closeCompanyDetails() {
      document.getElementById('company-details-modal').style.display = 'none';
    }

    /*********************************************************
     * 24) İş Detayları Modalı
     *********************************************************/
    function showJobDetails(entry) {
      const modal = document.getElementById('job-details-modal');
      const content = document.getElementById('job-details-content');
      let islemText = 'Seçilen işlem yok';
      if (entry.islem && entry.islem.length > 0) {
        islemText = entry.islem.join(', ');
      }
      content.innerHTML = `<h3>İş Detayı</h3>
        <p><strong>Tarih:</strong> ${entry.date}</p>
        <p><strong>Açıklama:</strong> ${entry.description}</p>
        <p><strong>Seçili Kutucuklar:</strong> ${islemText}</p>`;
      modal.style.display = 'block';
    }

    function closeJobDetails() {
      document.getElementById('job-details-modal').style.display = 'none';
    }

    /*********************************************************
     * 25) Onay Modalı İşlemleri
     *********************************************************/
    function openConfirmation(action, index) {
      pendingAction = action;
      pendingIndex = index;
      document.getElementById('confirmation-modal').style.display = 'flex';
    }

    document.getElementById('confirm-yes').addEventListener('click', function() {
      if (pendingAction === 'delete') {
        deleteEntry(pendingIndex);
      } else if (pendingAction === 'edit') {
        editEntry(pendingIndex);
        showToast('Düzenleme moduna alındı!');
      }
      closeConfirmation();
    });

    document.getElementById('confirm-no').addEventListener('click', function() {
      showToast('İşlem iptal edildi!');
      closeConfirmation();
    });

    function closeConfirmation() {
      pendingAction = null;
      pendingIndex = null;
      document.getElementById('confirmation-modal').style.display = 'none';
    }

    /*********************************************************
     * 26) Grafik Altındaki Firma Kutuçuklarını Oluşturma
     *********************************************************/
    function renderPerFirmCurrencyTotals(sortedFirms) {
      // sortedFirms: [ [firm, totalValueInTL], ... ] (büyükten küçüğe)
      const container = document.getElementById('currency-totals');
      container.innerHTML = '';
      if (sortedFirms.length === 0) return;

      // En yüksek değeri bulalım (en çok iş verenler)
      const maxValue = sortedFirms[0][1];
      topFirmNames = []; // Sıfırlıyoruz

      // Birden fazla firma aynı maxValue'ya sahip olabilir
      sortedFirms.forEach(([firm, value]) => {
        // Bu firmaya ait TL, USD, EUR toplamlari
        const totals = getFirmTotals(firm);
        let starHTML = '';
        if (value === maxValue) {
          starHTML = '<span class="star-blink">★</span>';
          topFirmNames.push(firm);
        }
        container.innerHTML += `
          <div class="currency-box">
            ${firm}${starHTML}<br/>
            TL: ${totals.TL.toFixed(2)}<br/>
            USD: ${totals.USD.toFixed(2)}<br/>
            EUR: ${totals.EUR.toFixed(2)}
          </div>
        `;
      });
    }

    /*********************************************************
     * 27) Firmalara Göre İş Performansı Grafiği (Chart.js)
     *     => Toplam parasal değere göre sıralar.
     *********************************************************/
    function renderFirmPerformanceChart() {
      // Her firmaya ait parasal değeri (TL cinsinden) hesaplayalım
      const firmValues = {};
      const firms = getUniqueFirms();
      firms.forEach(firm => {
        firmValues[firm] = calcFirmValue(firm); // TL cinsinden
      });
      // [ [firma, TLdeger], [firma, TLdeger], ... ]
      let sortedFirms = Object.entries(firmValues).sort((a, b) => b[1] - a[1]);
      // Grafikteki etiketler ve veriler
      const labels = sortedFirms.map(item => item[0]);
      const dataValues = sortedFirms.map(item => item[1]);
      // En büyük firmaya pembe ya da farklı bir renk, geri kalanına mavi vs. istersen
      // Biz 0. index için pembe, diğerleri için mavi koyalım
      const colors = sortedFirms.map((item, index) =>
        index === 0 ? 'rgba(255, 99, 132, 0.8)' : 'rgba(54, 162, 235, 0.8)'
      );

      // Dinamik genişlik
      const canvas = document.getElementById('firm-performance-chart');
      canvas.width = Math.max(600, labels.length * 80);

      // Daha önce oluşturulmuş grafik varsa yok edelim
      if (window.firmPerformanceChart) {
        window.firmPerformanceChart.destroy();
      }

      const ctx = canvas.getContext('2d');
      window.firmPerformanceChart = new Chart(ctx, {
        type: 'bar',
        data: {
          labels: labels,
          datasets: [{
            label: 'Toplam Parasal Değer (TL cinsinden)',
            data: dataValues,
            backgroundColor: colors,
            borderColor: colors.map(color => color.replace('0.8', '1')),
            borderWidth: 1
          }]
        },
        options: {
          scales: {
            y: {
              beginAtZero: true,
              ticks: { precision: 0 }
            }
          },
          plugins: {
            legend: { display: false },
            title: {
              display: true,
              text: 'Firmalara Göre İş Performansı (TL Karşılığı)'
            }
          }
        }
      });

      // Grafik altındaki her firmanın toplam verilerini göster
      renderPerFirmCurrencyTotals(sortedFirms);

      // "Yapılan İşler" tablosunda da yıldız görünmesi için loadEntries'i tekrar çağırıyoruz
      // (Filtre vs. bozulmaması için, anlık tabloyu koruyalım.)
      loadEntries();
    }

    /*********************************************************
     * 28) Sayfa Yüklendiğinde
     *********************************************************/
    window.onload = function() {
      loadEntries();
      loadFirms();
      loadCompanyLastEntry();
      updateTotalAmounts();
      renderFirmPerformanceChart();
    };
  </script>

  <!-- Chart.js Kütüphanesi -->
  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
</body>
</html>
