# Kkros-2.3-Kakarobot-IoTA
Kkros 2.3 merupakan Operating System untuk Robot Line Follower Kakarobot IoTA

# KKRos 2.3 – Panduan Upload ke Robot YPF IoTA

Panduan *step by step* untuk meng-upload (flash) sistem operasi **KKRos 2.3** ke robot **KAKAROBOT YPF IoTA** menggunakan **Espressif Flash Download Tools**.

> 🇬🇧 *English summary: this guide explains how to flash KKRos 2.3 onto the KAKAROBOT YPF IoTA robot (ESP32) using Espressif Flash Download Tools v3.6.8. See the [English Quick Reference](#english-quick-reference) at the bottom.*

---

## Daftar Isi

- [Varian Robot](#varian-robot)
- [Kebutuhan](#kebutuhan)
- [Daftar File & Alamat Flash](#daftar-file--alamat-flash)
- [Langkah Upload](#langkah-upload)
- [Pengaturan Flash Download Tools](#pengaturan-flash-download-tools)
- [Masuk ke Mode Bootloader](#masuk-ke-mode-bootloader)
- [Tips Jika Gagal](#tips-jika-gagal)
- [English Quick Reference](#english-quick-reference)
- [Sosial Media](#sosial-media)

---

## Varian Robot

| Varian | Cara Koneksi ke Komputer | Tombol Bootloader |
|---|---|---|
| **YPF IoTA Module** | Kabel USB | **Reset + Plus** |
| **YPF IoTA Non-Module** | USB Serial to TTL ke pin Serial pada robot | **Reset + Back** |

---

## Kebutuhan

- Komputer Windows (aplikasi berupa `flash_download_tools.exe`)
- **Espressif Flash Download Tools** (versi pada panduan ini: **v3.6.8**)
  Unduh dari halaman resmi Espressif: <https://www.espressif.com/en/support/download/other-tools>
- 4 file `.bin` KKRos 2.3 (lihat tabel di bawah)
- Kabel USB (varian Module) **atau** USB Serial to TTL (varian Non-Module)

---

## Daftar File & Alamat Flash

Masukkan **4 file** berikut pada alamat (*address*) yang sesuai:

| No | File | Alamat |
|----|------|--------|
| 1 | `boot_app0.bin` | `0xE000` |
| 2 | `bootloader_dio_80m.bin` | `0x1000` |
| 3 | `KKRos.IoTA.bin` **atau** `IOTA_Rev.0.1.module.bin` | `0x10000` |
| 4 | `KKRos.IoTA.partition.bin` **atau** `IOTA_Rev.0.1.partition.bin` | `0x8000` |

> ⚠️ Pastikan **keempat kotak centang** di sebelah kiri tiap baris dalam keadaan tercentang dan alamat diisi persis seperti tabel di atas.

---

## Langkah Upload

1. **Siapkan** aplikasi *Espressif Download Tools*.
2. **Jalankan** program `flash_download_tools.exe`.
3. Pilih **ESP32 DownloadTool**.

   ![Pilih ESP32 DownloadTool](docs/images/03-pilih-esp32.png)

4. **Masukkan 4 file `.bin`** yang telah disiapkan, lengkap dengan alamatnya (lihat [tabel file](#daftar-file--alamat-flash)).
5. Atur **SPI SPEED, SPI MODE, FLASH SIZE, COM, dan BAUD** sesuai bagian [Pengaturan](#pengaturan-flash-download-tools).
6. **Hubungkan robot** ke komputer:
   - **YPF IoTA Module** → kabel USB
   - **YPF IoTA Non-Module** → USB Serial to TTL ke pin Serial pada robot
7. **Masuk ke mode Bootloader** sesuai varian robot (lihat [caranya](#masuk-ke-mode-bootloader)).
8. Tekan **START** untuk memulai proses upload.

   ![Tampilan ESP32 Download Tool](docs/images/08-download-tool.png)

---

## Pengaturan Flash Download Tools

Sesuai tangkapan layar pada panduan:

| Parameter | Nilai |
|---|---|
| SPI SPEED | **40 MHz** |
| SPI MODE | **DIO** |
| FLASH SIZE | **32 Mbit** |
| COM | Sesuaikan dengan port robot di komputer Anda (contoh pada panduan: `COM8`) |
| BAUD | **921600** |

Informasi yang terdeteksi pada contoh (*DETECTED INFO*): flash devID `4016h`, QUAD 32 Mbit, crystal 40 MHz.

> 💡 Nomor COM berbeda di tiap komputer. Cek di **Device Manager → Ports (COM & LPT)**.

---

## Masuk ke Mode Bootloader

### YPF IoTA Module

1. Tekan dan tahan tombol **Reset** + tombol **Plus** secara bersamaan.
2. **Lepas tombol Reset** terlebih dahulu.
3. Kemudian lepas tombol **Plus**.

### YPF IoTA Non-Module

1. Tekan dan tahan tombol **Reset** + tombol **Back** secara bersamaan.
2. **Lepas tombol Reset** terlebih dahulu.
3. Kemudian lepas tombol **Back**.

Setelah itu, tekan **START** pada Flash Download Tools.

---

## Tips Jika Gagal

- Pastikan port **COM** yang dipilih benar dan robot terdeteksi di komputer.
- Ulangi urutan masuk mode Bootloader (lepas **Reset** dulu, baru tombol **Plus/Back**).
- Periksa kembali keempat file, alamat flash, dan pengaturan SPI/FLASH SIZE/BAUD.
- Pastikan kabel USB mendukung transfer data (bukan hanya pengisian daya).
- Jika masih gagal, coba turunkan nilai **BAUD**.

---

## English Quick Reference

**Requirements:** Espressif Flash Download Tools v3.6.8 (select *ESP32 DownloadTool*), USB cable (Module) or USB-to-TTL serial adapter (Non-Module).

**Flash layout:**

| File | Address |
|------|---------|
| `boot_app0.bin` | `0xE000` |
| `bootloader_dio_80m.bin` | `0x1000` |
| `KKRos.IoTA.bin` or `IOTA_Rev.0.1.module.bin` | `0x10000` |
| `KKRos.IoTA.partition.bin` or `IOTA_Rev.0.1.partition.bin` | `0x8000` |

**Settings:** SPI SPEED 40 MHz · SPI MODE DIO · FLASH SIZE 32 Mbit · BAUD 921600 · COM = your robot's port.

**Bootloader mode:** hold **Reset + Plus** (Module) or **Reset + Back** (Non-Module), release **Reset** first, then the other button. Click **START**.

---

## Sosial Media

Jangan lupa follow sosial media KAKAROBOT:

- Instagram: [@Kakarobot](https://www.instagram.com/kakarobot)
- YouTube: Kakarobot ID
- Facebook: Kakarobot
