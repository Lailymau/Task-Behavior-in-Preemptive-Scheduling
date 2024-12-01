# 🌟 Exercise 4 - Gain a good understanding of task behaviour where a priority preemptive scheduling policy is used.

Latihan ini dirancang untuk memahami perilaku multitasking dalam sistem operasi real-time (RTOS) menggunakan kebijakan penjadwalan preemptive priority. Eksperimen ini memanfaatkan STM32 dan FreeRTOS untuk mengamati pengaruh prioritas tugas terhadap urutan eksekusi.

---

## 🎯 Tujuan
- ✅ Memahami cara kerja **preemptive priority scheduling** pada FreeRTOS.
- ✅ Mengamati bagaimana tugas dengan prioritas tinggi menginterupsi tugas dengan prioritas lebih rendah.
- ✅ Mempraktikkan pembuatan dan pengelolaan tugas (tasks) di FreeRTOS.

---

## 📂 Node Diagram
![image](https://github.com/user-attachments/assets/a7f3902d-4e93-4dd5-8c64-bacca9fcf3bc)

---

## 🛠️ Peralatan
- 🖥️ **Board STM32** (konfigurasi sesuai file `.ioc`).
- 💡 **LED**:
  - **Green LED**: Untuk tugas prioritas normal.
  - **Red LED**: Untuk tugas prioritas lebih tinggi.
- 🔌 **Kabel koneksi**.
- 🛡️ **Mini debugger**.

---

## 🚀 Langkah Implementasi
1. **🛠️ Konfigurasi STM32CubeMX**:
   - Pilih board sesuai file `.ioc`.
   - Aktifkan FreeRTOS di tab Middleware.
   - Konfigurasi GPIO untuk LED:
     - `led1` dan `led2`: Tugas Green LED.
     - `led3` dan `led4`: Tugas Red LED.
   - Generate kode untuk STM32CubeIDE.

2. **💻 Implementasi Tugas di FreeRTOS**:
   - 🔹 **Green LED Task**:
     - Prioritas: Normal.
     - Berkedip 8 kali setiap 500 ms, kemudian delay selama 6 detik.
   - 🔸 **Red LED Task**:
     - Prioritas: Above Normal.
     - Berkedip 10 kali setiap 50 ms, kemudian delay selama 1,5 detik.
   - Gunakan fungsi `osThreadNew()` untuk membuat tugas dan `vTaskDelay()` untuk pengaturan jeda.

3. **🛠️ Kompilasi dan Flash**:
   - Kompilasi proyek menggunakan STM32CubeIDE.
   - Flash kode ke board STM32 menggunakan debugger.

4. **👀 Pengamatan**:
   - Perhatikan bagaimana Green LED sering diinterupsi oleh Red LED karena perbedaan prioritas.

---

## 🌟 Output
- 🟢 **Green LED**:
  - Berkedip 8 kali setiap 500 ms, dengan delay 6 detik.
  - Eksekusinya sering diinterupsi oleh Red LED karena prioritas lebih rendah.
- 🔴 **Red LED**:
  - Berkedip 10 kali setiap 50 ms, dengan delay 1,5 detik.
  - Selalu memiliki prioritas lebih tinggi dan tidak terganggu oleh tugas lain.

---

## 📊 Hasil Percobaan
https://github.com/user-attachments/assets/797dbc35-696e-4f98-804e-01c99aa5812b
