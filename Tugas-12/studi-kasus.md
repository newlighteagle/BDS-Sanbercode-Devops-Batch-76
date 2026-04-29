** Studi Kasus (Wajib Dijawab) **
Tech Lead kalian bertanya:

_"Kenapa sih kita harus rajin melakukan apt purge atau menghapus servis yang nggak kepakai kayak MySQL/Postgres tadi sebelum kita instal SSL dan rilis ke publik? Apa hubungannya sama keamanan dan performa server?"_

Pertanyaan: Berikan jawaban analisis kalian secara singkat dan tepat

<hr>

# Analisis Hardening Server (Go-Live Preparation)

### 1. Keamanan: Memperkecil _Attack Surface_

Setiap servis yang berjalan membuka _port_ dan potensi celah keamanan. Menghapus servis yang tidak terpakai (seperti MySQL/Postgres) memastikan tidak ada "pintu belakang" yang tidak terurus atau lupa di-_patch_ yang bisa dieksploitasi oleh pihak luar.

### 2. Performa: Optimasi _Resource_

Servis database tetap mengonsumsi RAM dan CPU meskipun dalam kondisi _idle_. Dengan melakukan `apt purge`, kita membebaskan sumber daya server sepenuhnya untuk menangani trafik aplikasi utama, sehingga performa lebih stabil saat rilis publik.

### 3. Stabilitas: Menghindari Konflik Konfigurasi

Melakukan pembersihan sebelum instalasi SSL memastikan lingkungan server dalam kondisi bersih (_Lean & Mean_). Ini mencegah potensi konflik dependensi atau _port_ (seperti port 80/443) yang bisa mengganggu konfigurasi _web server_ dan sertifikat keamanan.

**Kesimpulan:**
Langkah ini adalah standar **Hardening** untuk memastikan kita hanya merilis servis yang esensial, aman, dan efisien secara sumber daya.
