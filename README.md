<!DOCTYPE html>
<html lang="id">
<head>
    <title>Reservasi Hotel Demo</title>
</head>
<body>
    <h2>Formulir Reservasi</h2>
    Nama: <input type="text" id="nama"><br>
    Email: <input type="email" id="email"><br>
    Telepon: <input type="tel" id="telepon"><br>
    Pembayaran: 
    <select id="pembayaran">
        <option>Kartu Kredit</option>
        <option>Transfer Bank</option>
        <option>E-Wallet</option>
    </select><br>
    <button onclick="simpanReservasi()">Konfirmasi Pemesanan</button>
    
    <hr>
    <button onclick="lihatReservasi()">Lihat Daftar Reservasi</button>
    <div id="daftarReservasi"></div>
    
    <script>
    function simpanReservasi() {
        let nama = document.getElementById('nama').value;
        let email = document.getElementById('email').value;
        let telepon = document.getElementById('telepon').value;
        let pembayaran = document.getElementById('pembayaran').value;
        let waktu = new Date().toLocaleString();

        let reservasi = JSON.parse(localStorage.getItem('reservasi')) || [];
        reservasi.push({nama, email, telepon, pembayaran, waktu});
        localStorage.setItem('reservasi', JSON.stringify(reservasi));
        alert("Reservasi berhasil!");
    }

    function lihatReservasi() {
        let reservasi = JSON.parse(localStorage.getItem('reservasi')) || [];
        if (reservasi.length === 0) {
            document.getElementById('daftarReservasi').innerHTML = "<p>Belum ada reservasi.</p>";
            return;
        }
        let html = "<h2>Daftar Reservasi</h2><table border='1'><tr><th>Nama</th><th>Email</th><th>Telepon</th><th>Pembayaran</th><th>Waktu</th></tr>";
        reservasi.forEach(function(data) {
            html += `<tr>
                <td>${data.nama}</td>
                <td>${data.email}</td>
                <td>${data.telepon}</td>
                <td>${data.pembayaran}</td>
                <td>${data.waktu}</td>
            </tr>`;
        });
        html += "</table>";
        document.getElementById('daftarReservasi').innerHTML = html;
    }
    </script>
</body>
</html>

    <h1>Reservasi Hotel ABC</h1>
    <p>Selamat datang di sistem reservasi hotel kami. Isi formulir di bawah untuk mencari kamar.</p>

    <!-- Formulir Pencarian -->
    <div class="form">
        <h2>Formulir Pencarian Kamar</h2>
        <label for="lokasi">Lokasi:</label>
        <input type="text" id="lokasi" placeholder="Misalnya: Jakarta" required><br><br>
        
        <label for="checkin">Tanggal Check-In:</label>
        <input type="date" id="checkin" required><br><br>
        
        <label for="checkout">Tanggal Check-Out:</label>
        <input type="date" id="checkout" required><br><br>
        
        <label for="tamu">Jumlah Tamu:</label>
        <select id="tamu">
            <option>1 Dewasa</option>
            <option>2 Dewasa</option>
            <option>2 Dewasa + 1 Anak</option>
            <option>4 Dewasa</option>
        </select><br><br>
        
        <button onclick="alert('Pencarian berhasil! Lihat hasil di bawah.')">Cari Kamar</button>
    </div>

    <!-- Daftar Hasil Pencarian -->
    <h2>Hasil Pencarian Kamar</h2>
    <div class="result">
        <h3>Hotel Edutel Hotel - Kamar Deluxe</h3>
        <p>Lokasi: Labuan Bajo | Fasilitas: WiFi Gratis, Sarapan, Kolam Renang</p>
        <p>Harga: Rp 450.000/malam | Rating: 4.5/5 (Berdasarkan 200 ulasan)</p>
        <p>Ulasan: "Kamar bersih dan nyaman, staf ramah." - Tamu Anonim</p>
        <button onclick="showBookingForm()">Pilih Kamar Ini</button>
    </div>
    
    <div class="result">
        <h3>Hotel Budget Inn - Kamar Standar</h3>
        <p>Lokasi: Labuan Bajo | Fasilitas: WiFi Gratis, Parkir</p>
        <p>Harga: Rp 250.000/malam | Rating: 3.8/5 (Berdasarkan 150 ulasan)</p>
        <p>Ulasan: "Harga murah, tapi fasilitas sederhana." - Tamu Anonim</p>
        <button onclick="showBookingForm()">Pilih Kamar Ini</button>
    </div>

    <!-- Formulir Pemesanan -->
    <div class="form" id="bookingForm" style="display:none;">
        <h2>Formulir Pemesanan</h2>
        <label for="nama">Nama Lengkap:</label>
        <input type="text" id="nama" placeholder="Masukkan nama Anda" required><br><br>
        
        <label for="email">Email:</label>
        <input type="email" id="email" placeholder="contoh@email.com" required><br><br>
        
        <label for="telepon">Nomor Telepon:</label>
        <input type="tel" id="telepon" placeholder="+62 812-3456-7890" required><br><br>
        
        <label for="pembayaran">Metode Pembayaran:</label>
        <select id="pembayaran">
            <option>Kartu Kredit</option>
            <option>Transfer Bank</option>
            <option>E-Wallet (GoPay)</option>
        </select><br><br>
        
        <p><strong>Total Biaya: Rp 900.000 (2 malam)</strong></p>
        <button onclick="alert('Reservasi berhasil! Nomor konfirmasi: ABC123. Email konfirmasi dikirim.')">Konfirmasi Pemesanan</button>
    </div>

    <p>Catatan: Ini adalah contoh simulasi. Kebijakan pembatalan: Gratis hingga 24 jam sebelum check-in.</p>

</body>
</html>
