# 🔍 Crackme Solutions

Repository ini berisi kumpulan solusi dan writeup hasil analisis beberapa challenge **CrackMe** dari **crackmes.one**. Setiap writeup menjelaskan proses reverse engineering yang dilakukan, mulai dari analisis program, tools yang digunakan, langkah-langkah penyelesaian, hingga hasil akhir.

---

## Identitas

| Keterangan | Isi |
|------------|-----|
| **Nama** | AISYAH NUR MAYA SILVIYANI |
| **NIM** | 24.83.1068 |
| **Kelas** | 24TK01 |

---

## Deskripsi

Repository ini dibuat sebagai dokumentasi proses belajar **Reverse Engineering** menggunakan berbagai tools analisis biner. Setiap challenge dikerjakan secara mandiri dan seluruh writeup ditulis berdasarkan hasil analisis sendiri.

Setiap folder berisi:

- README.md (writeup)
- Screenshot proses analisis
- Screenshot hasil
- File pendukung lainnya

---

## Tools yang Digunakan

- Ghidra
- x64dbg
- Detect It Easy (DIE)
- PE-bear (jika diperlukan)
- Strings
- Windows Command Prompt

---

## Daftar CrackMe

| Nama | Sumber | Level | Tools | Status |
|------|---------|-------|-------|--------|
| CR1 | https://crackmes.one/ | Easy | Ghidra | ✅ Selesai |
| CR2 | https://crackmes.one/ | Easy | Ghidra | ✅ Selesai |
| CR3 | https://crackmes.one/ | Medium | Ghidra | ✅ Selesai |

> **Catatan:** Link pada kolom **Sumber** mengarah ke halaman challenge yang digunakan sebagai referensi.

---

## Struktur Repository

```
crackme-solutions/
│
├── CR1/
│   ├── README.md
│   ├── crackme.png
│   ├── ghidra (function).png
│   └── hasil.png
│
├── CR2/
│   ├── README.md
│   ├── cr2.png
│   ├── funcion_validasi.png
│   └── hasil.png
│
├── CR3/
│   ├── README.md
│   ├── cr3.png
│   ├── function menunjukan passwd.png
│   └── 5eb1513333c5d47611746546.zip
│
└── README.md
```

---

## Isi Writeup

Setiap writeup memuat informasi berikut:

- Informasi challenge
- Link sumber crackme
- Level challenge
- Tools yang digunakan
- Analisis awal file
- Proses reverse engineering
- Fungsi penting yang ditemukan
- Screenshot Ghidra/x64dbg yang telah diberi anotasi
- Langkah mendapatkan password/flag
- Hasil akhir
- Kesimpulan

---

## Tujuan

Repository ini dibuat untuk:

- Mempelajari dasar Reverse Engineering.
- Melatih analisis executable menggunakan Ghidra dan debugger.
- Mendokumentasikan proses penyelesaian CrackMe secara sistematis.
- Menjadi referensi pembelajaran pribadi mengenai teknik analisis program.

---

## Catatan

- Seluruh writeup merupakan hasil analisis dan pemahaman sendiri.
- Referensi digunakan hanya sebagai bahan pembelajaran dan tidak disalin secara langsung.
- Screenshot yang disertakan telah diberi penjelasan pada bagian kode yang relevan untuk memperjelas proses analisis.
