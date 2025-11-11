Tugas Basis Data – Database KebunSayur

Repository ini berisi tugas Basis Data yang mencakup:

Membuat 1 database
Membuat minimal 3 tabel
Insert 15 data di setiap tabel
Menggunakan query WHERE dan BETWEEN

1. Nama Database KebunSayur
2. Struktur Tabel :
  tabel petani :
  - id_petani (INT, PRIMARY KEY)
  - nama (VARCHAR)
  - alamat (VARCHAR)
  - no_hp (VARCHAR)

  tabel sayur :
  - id_sayur (INT, PRIMARY KEY)
  - nama_sayur (VARCHAR)
  - wantu_tanam(INT)
  - waktu_panen (INT)
  - jenis_tanah (VARCHAR)

  tabel panen :
  - id_panen (INT, PRIMARY KEY)
  - id_sayur (INT)
  - id_petani (INT)
  - jumlah_kg (INT)
  - tanggal_panen (DATE)

3. Kodingan SQL :
    -Membuat database :
      CREATE DATABASE KebunSayur;
      USE KebunSayur;

4. membuat tabel :
   CREATE TABLE petani (
    id_anggota INT(11) PRIMARY KEY,
    nama VARCHAR(50),
    alamat VARCHAR(100),
    no_hp VARCHAR(15)
   );

 CREATE TABLE sayur (
    id_sayur INT(11) PRIMARY KEY,
    nama_sayur VARCHAR(50),
    waktu_tanam INT(11),
    waktu_panen INT(11),
    jenia_tanah VARCHAR(50)
 );

 CREATE TABLE panen (
    id_panen INT(11) PRIMARY KEY,
    id_sayur INT(11),
    id_petani INT(11),
    jumlah_kg INT(11),
    tanggal_panen DATE
 );

5. Insert 15 Data ke Setiap Tabel
    Tabel petani :
   INSERT INTO petani (id_petani, nama, alamat, no_hp) VALUES
    (1, 'Pak Budi', 'Desa Mekar Sari', '081200001'),
    (2, 'bu siti', 'Desa Harapan Baru', '081200002'),
    (3, 'Pak joko', 'Desa Sukamuju', '081200003'),
    (4, 'Bu rina', 'Desa Tanete', '081200004'),
    (5, 'Pak andi', 'Desa galung', '081200005'),
    (6, 'Bu wati', 'Desa lambe', '081200006'),
    (7, 'Pak umar', 'Desa pao-pao', '081200007'),
    (8, 'Bu mira', 'Desa soreang', '081200008'),
    (9, 'Pak ahmad', 'Desa somba', '081200009'),
    (10, 'Bu lilis', 'Desa rea timur', '0812000010'),
    (11, 'Pak dani', 'Desa padang', '0812000011'),
    (12, 'Bu Tina', 'Desa Baku', '081200012'),
    (13, 'Pak hasan', 'Desa pekkabata', '081200013'),
    (14, 'Bu rosi', 'Desa laliko', '081200014'),
    (15, 'Pak rafi', 'Desa tande', '081200015');

  Tabel sayur :
    INSERT INTO sayur (id_sayur, nama_sayur, waktu_tanam, waktu_panen, jenis_tanah) VALUES
    (1, 'Bayam', 7, 25, 'Lempung'),
    (2, 'Kangkung', 5, 21, 'Gembur'),
    (3, 'Selada', 10, 35, 'Berpasir'),
    (4, 'Sawi', 8, 30, 'Gembur'),
    (5, 'Tomat', 15, 70, 'Lempung'),
    (6, 'Cabai', 20, 80, 'Lempung Berpasir'),
    (7, 'Terong', 18, 75, 'Lempung'),
    (8, 'Timun', 12, 55, 'Berpasir'),
    (9, 'Wortel', 14, 90, 'Berpasir'),
    (10, 'Bawang Merah', 10, 60, 'Lempung Berpasir'),
    (11, 'Brokoli', 12, 70, 'Liat'),
    (12, 'Kubis', 15, 90, 'Lempung'),
    (13, 'Seledri', 10, 60, 'Lempung Berpasir'),
    (14, 'Pakchoy', 7, 30, 'Gembur'),
    (15, 'Kacang Panjang', 12, 55, 'Lempung');

  Tabel panen :
    INSERT INTO panen (id_panen, id_sayur, id_petani, jumlah_kg, tanggal_panen) VALUES
    (1, 1, 1, 12, '2025-01-10'),
    (2, 2, 2, 15, '2025-01-12'),
    (3, 3, 3, 10, '2025-01-15'),
    (4, 4, 4, 20, '2025-01-17'),
    (5, 5, 5, 18, '2025-01-20'),
    (6, 6, 6, 25, '2025-01-22'),
    (7, 7, 7, 17, '2025-01-15'),
    (8, 8, 8, 30, '2025-01-28'),
    (9, 9, 9, 22, '2025-01-30'),
    (10, 10, 10, 14, '2025-01-01'),
    (11, 11, 11, 12, '2025-01-03'),
    (12, 12, 12, 19, '2025-01-05'),
    (13, 13, 13, 15, '2025-01-07'),
    (14, 14, 14, 16, '2025-01-09'),
    (15, 15, 15, 21, '2025-01-11');

   5. Query WHERE dan BETWEEN
      where ;
       SELECT * FROM panen
       WHERE jumlah_kg > 20;

       SELECT * FROM sayur
       WHERE waktu_panen > 60;

       SELECT * FROM sayur
       WHERE waktu_tanam BETWEEN 7 AND 12;

       SELECT * FROM panen
       WHERE tanggal_panen BETWEEN '2025-01-10' AND '2025-01-20';

      SELECT * FROM petani
       WHERE id_petani BETWEEN 5 AND 10;

      SELECT * FROM sayur
       WHERE waktu_panen BETWEEN 30 AND 70;

      between :
      SELECT p.id_panen, s.nama_sayur, t.nama AS nama_petani, p.jumlah_kg
      FROM panen p
      JOIN sayur s ON p.id_sayur = s.id_sayur
      JOIN petani t ON p.id_petani = t.id_petani
      WHERE p.jumlah_kg BETWEEN 10 AND 20;

      SELECT p.id_panen, s.nama_sayur, p.tanggal_panen
      FROM panen p
      JOIN sayur s ON p.id_sayur = s.id_sayur
      WHERE p.tanggal_panen BETWEEN '2025-01-01' AND '2025-01-31';

      SELECT * FROM petani
      WHERE nama LIKE 'Bu%';
   
