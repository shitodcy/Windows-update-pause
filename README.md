# Windows Update - Pause Limit Extender

Skrip Registry Windows (`.reg`) ini digunakan untuk mengubah **batas maksimum** jumlah hari Anda bisa menjeda (pause) pembaruan Windows.

Secara default, Windows mungkin hanya mengizinkan Anda menjeda pembaruan selama 5 minggu (35 hari). Dengan skrip ini, Anda dapat mengatur batas tersebut ke nilai yang jauh lebih tinggi, misalnya 365 hari atau lebih.

**Penting:** Skrip ini menargetkan pengaturan "Flight" (`FlightSettingsMaxPauseDays`), yang berarti kemungkinan besar **hanya berfungsi pada build Windows Insider** (Dev, Beta, Canary) dan mungkin tidak berpengaruh pada Windows versi rilis stabil.

---

## 1. Cara Mengatur Durasi Pause

Anda harus mengedit file `.reg` **sebelum** menjalankannya untuk mengatur durasi jeda yang Anda inginkan.

1.  **Jangan** klik dua kali file-nya dulu.
2.  **Klik Kanan** pada file `.reg` (misal `pause-update.reg`) dan pilih **Edit**. File tersebut akan terbuka di Notepad.
3.  Anda akan melihat baris yang mirip seperti ini:
    ```reg
    "FlightSettingsMaxPauseDays"=dword:000001c4
    ```
4.  Nilai `000001c4` adalah angka **Heksadesimal**. Nilai ini mewakili jumlah hari.
    * `000001c4` (Heksadesimal) = **452** (Desimal). Ini berarti batas jeda diatur ke 452 hari.

### Mengubah Nilai

Misalkan Anda ingin mengubahnya menjadi **365 hari**:

1.  Anda perlu mengonversi **365** (Desimal) ke **Heksadesimal**.
2.  Gunakan kalkulator (atau [Google](https://www.google.com/search?q=365+decimal+to+hex)):
    **365 (Desimal) = 16D (Heksadesimal)**
3.  Ubah nilai `dword` di file `.reg` Anda:

    **Sebelum:**
    ```reg
    "FlightSettingsMaxPauseDays"=dword:000001c4
    ```

    **Sesudah (untuk 365 hari):**
    ```reg
    "FlightSettingsMaxPauseDays"=dword:0000016D
    ```
4.  **Simpan (Save)** file Notepad tersebut dan tutup.

---

## 2. Cara Penggunaan

Setelah Anda menyimpan file `.reg` dengan nilai hari yang Anda inginkan:

1.  **Jalankan Skrip:** Klik dua kali pada file `.reg` Anda.
2.  **Peringatan UAC:** Jika diminta oleh User Account Control (UAC), klik **Yes**.
3.  **Peringatan Registry:** Registry Editor akan bertanya apakah Anda yakin ingin melanjutkan. Klik **Yes**.
4.  **Selesai:** Anda akan melihat pesan yang mengonfirmasi bahwa kunci telah berhasil ditambahkan ke registri. Klik **OK**.

### ❗ Langkah Terakhir (Paling Penting)

Menjalankan skrip ini **TIDAK SECARA OTOMATIS** menjeda pembaruan Anda. Ini hanya **MENGUBAH BATAS MAKSIMUM** di menu pengaturan.

Anda masih harus menjeda pembaruan secara manual:

1.  Buka **Settings** (Pengaturan).
2.  Buka **Windows Update**.
3.  Cari opsi **Pause updates** (Jeda pembaruan).
4.  Klik pada menu *dropdown* untuk memilih durasi jeda. Anda sekarang akan melihat opsi untuk menjeda pembaruan hingga **[Jumlah Hari]** yang Anda tetapkan (misalnya, "Pause for 365 days").
5.  Pilih durasi yang Anda inginkan untuk mulai menjeda pembaruan.

---

> [!WARNING]
> **PERINGATAN**
>
> * Anda mengedit Windows Registry dengan risiko Anda sendiri. Kesalahan dalam mengedit registri dapat menyebabkan ketidakstabilan sistem.
> * Seperti yang disebutkan, ini kemungkinan besar hanya berfungsi pada Windows Insider dan tidak ada jaminan akan berfungsi pada semua versi atau build Windows.
