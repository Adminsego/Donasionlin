-- Membuat tabel admin
CREATE TABLE admin (
    id_admin INT AUTO_INCREMENT PRIMARY KEY,
    nama VARCHAR(100) NOT NULL,
    email VARCHAR(100) NOT NULL UNIQUE,
    password VARCHAR(255) NOT NULL
);

-- Membuat tabel bansos
CREATE TABLE bansos (
    id_bansos INT AUTO_INCREMENT PRIMARY KEY,
    nama_bansos VARCHAR(100) NOT NULL,
    deskripsi TEXT
);

-- Membuat tabel donatur
CREATE TABLE donatur (
    id_donatur INT AUTO_INCREMENT PRIMARY KEY,
    nama VARCHAR(100) NOT NULL,
    email VARCHAR(100) NOT NULL UNIQUE,
    no_telepon VARCHAR(15) UNIQUE
);

-- Membuat tabel penerima
CREATE TABLE penerima (
    id_penerima INT AUTO_INCREMENT PRIMARY KEY,
    nama VARCHAR(100) NOT NULL,
    alamat TEXT,
    no_telepon VARCHAR(15) UNIQUE
);

-- Membuat tabel donasi penyaluran
CREATE TABLE donasipenyaluran (
    id_donasi INT AUTO_INCREMENT PRIMARY KEY,
    id_donatur INT NOT NULL,
    id_penerima INT NOT NULL,
    jumlah_donasi DECIMAL(10, 2) NOT NULL,
    tanggal_donasi DATE NOT NULL,
    FOREIGN KEY (id_donatur) REFERENCES donatur(id_donatur) ON DELETE CASCADE ON UPDATE CASCADE,
    FOREIGN KEY (id_penerima) REFERENCES penerima(id_penerima) ON DELETE CASCADE ON UPDATE CASCADE
);

-- Membuat tabel program donasi
CREATE TABLE programdonasi (
    id_program INT AUTO_INCREMENT PRIMARY KEY,
    nama_program VARCHAR(100) NOT NULL,
    deskripsi TEXT,
    target_donasi DECIMAL(10, 2) NOT NULL
);

-- Menambahkan data awal ke tabel admin
INSERT INTO admin (nama, email, password) VALUES
('Admin1', 'admin1@example.com', 'password123'),
('Admin2', 'admin2@example.com', 'password456');

-- Menambahkan data awal ke tabel bansos
INSERT INTO bansos (nama_bansos, deskripsi) VALUES
('Bansos Pendidikan', 'Bantuan untuk pendidikan anak-anak'),
('Bansos Kesehatan', 'Bantuan untuk biaya pengobatan');

-- Menambahkan data awal ke tabel donatur
INSERT INTO donatur (nama, email, no_telepon) VALUES
('Donatur1', 'donatur1@example.com', '081234567890'),
('Donatur2', 'donatur2@example.com', '081234567891');

-- Menambahkan data awal ke tabel penerima
INSERT INTO penerima (nama, alamat, no_telepon) VALUES
('Penerima1', 'Jl. Kebon Jeruk No.1', '081234567892'),
('Penerima2', 'Jl. Mangga Dua No.2', '081234567893');

-- Menambahkan data awal ke tabel donasi penyaluran
INSERT INTO donasipenyaluran (id_donatur, id_penerima, jumlah_donasi, tanggal_donasi) VALUES
(1, 1, 500000.00, '2025-01-01'),
(2, 2, 300000.00, '2025-01-02');

-- Menambahkan data awal ke tabel program donasi
INSERT INTO programdonasi (nama_program, deskripsi, target_donasi) VALUES
('Program Beasiswa', 'Program untuk memberikan beasiswa kepada siswa berprestasi', 10000000.00),
('Program Bantuan Kesehatan', 'Program untuk membantu pasien yang membutuhkan', 15000000.00);

-- Menampilkan data dari tabel-tabel
SELECT * FROM admin;
SELECT * FROM bansos;
SELECT * FROM donatur;
SELECT * FROM penerima;
SELECT * FROM donasipenyaluran;
SELECT * FROM programdonasi;
