# TryHackMe — Pengantar Keamanan Serangan (Offensive Security Intro)
**Tanggal:** 24 Juni 2026  
**Tingkat:** Mudah  
**Status:** ✅ Selesai  
**Flag:** `BANK-HACKED`

---

## 🎯 Tujuan Room
Memahami konsep dasar offensive security dengan cara mensimulasikan serangan terhadap website bank palsu (FakeBank) secara legal di environment yang aman.

---

## 📖 Yang Gw Pelajari

### Apa itu Offensive Security?
Offensive security adalah pendekatan keamanan siber di mana kita **berpikir dan bertindak seperti hacker** — mencari celah dan kelemahan sistem sebelum orang jahat menemukannya duluan. Inilah yang dilakukan seorang **Penetration Tester / Red Team** secara legal.

### Konsep Utama
- **Directory Brute Force** — teknik menemukan halaman/direktori tersembunyi di sebuah website yang tidak terlihat oleh user biasa
- **Hidden Admin Panel** — banyak website punya halaman admin yang tidak ditampilkan di menu, tapi tetap bisa diakses kalau tau URL-nya
- **Unauthorized Access Simulation** — dalam environment legal, kita bisa simulasikan bagaimana attacker mengakses sistem tanpa izin

---

## 🛠️ Tools Yang Dipakai

### DIRB
Tool untuk melakukan **directory brute force** — mencoba satu per satu kemungkinan URL/direktori di sebuah website menggunakan wordlist.

```bash
dirb http://fakebank.thm
```

**Cara kerja:**
1. DIRB mengambil daftar kata (wordlist) yang sudah ada bawaannya
2. Mencoba akses satu per satu: `http://fakebank.thm/admin`, `http://fakebank.thm/login`, dst
3. Kalau halaman ditemukan (status 200), DIRB akan menampilkannya di output

**Hasil yang ditemukan:**
```
/bank-transfer    (Status: 200)
```

---

## 📋 Langkah-Langkah yang Gw Lakuin

**Step 1** — Jalankan DIRB untuk scan direktori FakeBank
```bash
dirb http://fakebank.thm
```

**Step 2** — Dari hasil scan, ditemukan halaman tersembunyi:
```
http://fakebank.thm/bank-transfer
```

**Step 3** — Akses halaman `/bank-transfer` di browser

**Step 4** — Pilih nomor rekening **8881**, transfer **$2000**

**Step 5** — Setelah transfer berhasil, muncul pop-up hijau dengan flag:
```
BANK-HACKED
```
