# Crackme 01 — Very Easy Crackme

## Informasi Crackme

| Keterangan | Detail |
|------------|--------|
| Nama | Very Easy Crackme |
| Author | vasa |
| Platform | Windows x64 |
| Bahasa | C/C++ |
| Difficulty | Easy (1.3) |
| Link | https://crackmes.one/crackme/66b8d5f1c5d2dd4d2f4b0d9f |

---

# Tujuan

Tujuan dari challenge ini adalah menemukan kombinasi **username** dan **password** yang dapat melewati proses validasi program.

Challenge ini termasuk kategori **Easy**, sehingga cocok digunakan untuk belajar dasar-dasar proses reverse engineering menggunakan Ghidra.

---

# Tools yang Digunakan

- Parrot Security OS
- Ghidra
- Python 3
- Terminal Linux

---

# Proses Analisis

## 1. Membuka Binary Menggunakan Ghidra

File executable dibuka menggunakan **Ghidra**, kemudian dilakukan proses **Auto Analysis**.

Selanjutnya saya mencari fungsi **main()** karena biasanya proses validasi password berada pada fungsi tersebut.

---

## 2. Analisis Fungsi main()

Setelah fungsi berhasil didecompile, terlihat bahwa program meminta dua buah input:

- Username
- Password

Kemudian terdapat beberapa fungsi string dari C seperti:

- `strcpy()`
- `strcat()`
- `strcmp()`

Dari sini dapat diketahui bahwa password tidak dibandingkan dengan string tetap, melainkan dibentuk terlebih dahulu menggunakan username yang dimasukkan oleh pengguna.

---

## 3. Analisis Logika Program

Potongan logika yang ditemukan adalah sebagai berikut:

```cpp
strcpy(local_10, "0xjfkD2");

puts("Enter Username:");
scanf("%30s", local_38);

puts("Enter Password:");
scanf("%30s", local_58);

strcpy(local_78, local_38);
strcat(local_78, local_10);

if(strcmp(local_58, local_78) == 0)
{
    puts("Password is correct.");
}
```

Dari kode tersebut dapat disimpulkan bahwa:

1. Program menyimpan string tetap

```
0xjfkD2
```

2. Username yang dimasukkan akan disalin ke buffer.

3. Program menambahkan string `"0xjfkD2"` di belakang username.

4. Hasil gabungan tersebut dibandingkan dengan password yang dimasukkan.

Secara sederhana logikanya adalah:

```
password = username + "0xjfkD2"
```

---

# Mengubah Logika C++ Menjadi Python

Agar lebih mudah dipahami, saya mengubah logika program C++ hasil dekompilasi menjadi Python.

Tujuan konversi ini bukan untuk melakukan cracking secara otomatis, melainkan untuk memahami alur program dengan lebih jelas.

Contoh implementasi:

```python
secret = "0xjfkD2"

username = input("Enter Username: ")
password = input("Enter Password: ")

expected_password = username + secret

if password == expected_password:
    print("Password is correct. Good job")
else:
    print("No, that's not it. Try again")
```

Dengan implementasi Python tersebut menjadi jauh lebih mudah memahami bagaimana proses validasi password bekerja.

---

# Hasil

Misalkan username yang digunakan adalah

```
ais
```

Maka password yang benar adalah

```
ais0xjfkD2
```

Karena program akan melakukan proses:

```
password = username + "0xjfkD2"
```

---

# Screenshot Analisis

## 1. Halaman Crackme

> **Tambahkan screenshot halaman challenge dari Crackmes.one di sini**

<p align="center">
<img src="images/challenge.png" width="900">
</p>

---

## 2. Analisis Menggunakan Ghidra

> **Tambahkan screenshot Ghidra yang sudah diberi anotasi mengenai proses strcpy(), strcat(), dan strcmp().**

<p align="center">
<img src="images/ghidra-analysis.png" width="900">
</p>

---

## 3. Implementasi Python

> **Tambahkan screenshot kode Python yang digunakan untuk memahami logika program.**

<p align="center">
<img src="images/python-convert.png" width="900">
</p>

---

## 4. Hasil Eksekusi

> **Tambahkan screenshot hasil program yang menunjukkan password berhasil diterima.**

<p align="center">
<img src="images/result.png" width="900">
</p>

---

# Kesimpulan

Challenge ini memperkenalkan konsep dasar reverse engineering terhadap proses validasi password.

Dari hasil analisis menggunakan Ghidra dapat diketahui bahwa program tidak menyimpan password lengkap, melainkan membentuk password berdasarkan username yang dimasukkan pengguna kemudian menambahkan string tetap **"0xjfkD2"**.

Mengubah hasil dekompilasi C++ ke dalam Python membantu saya memahami fungsi-fungsi string seperti `strcpy()`, `strcat()`, dan `strcmp()` tanpa harus membaca kode hasil dekompilasi yang lebih kompleks.

Melalui challenge ini saya mempelajari cara:

- menggunakan Ghidra untuk melakukan analisis static,
- membaca hasil dekompilasi fungsi `main()`,
- memahami penggunaan fungsi string pada bahasa C,
- mengidentifikasi proses validasi password,
- serta menerjemahkan logika program ke Python agar lebih mudah dipahami.

---

# Flag / Password

Contoh:

Username

```
ais
```

Password

```
ais0xjfkD2
```
