# MyPortfolio

## Tampilan Setiap Section / Fitur

1. Navbar

   Bagian paling atas website (fixed-top) yang berisi
   a. Logo / Nama: MyPortfolio
   c. Menu navigasi, yitu home, about, dokumentasi, dan sertifikat


2. Home

   Tampilan pertama saat website dibuka

   a. Foto profil 
   b. Nama
   c. Tagline
   d. Tombol scroll down


3. About Me
   
   a. Deskripsi diri
   
   b. pengalaman organisasi
   
   c. skill level

   Skill ditampilkan dalam bentuk progress bar dengan persentase:
   
   a. Manajemen Waktu – 90%
   
   b. Kerjasama Tim – 85%
   
   c. Komunikasi – 75%


5. Sertifikat

   Menampilkan sertifikat dalam bentuk grid 4 kolom

   a. Gambar sertifikat
   
   b. Judul
   
   c. Deskripsi


7. Footer
   
   © 2026 - Elvira Agustin | Portfolio Website


## Penjelasan Code Setiap Section / Fitur


1. NAVBAR
   
<nav class="navbar navbar-expand-lg navbar-dark custom-navbar fixed-top shadow">
    <div class="container">

        <!-- Logo / Brand -->
        <a class="navbar-brand fw-bold" href="#">MyPortfolio</a>

        <!-- Button toggle untuk mobile -->
        <button class="navbar-toggler" 
                type="button" 
                data-bs-toggle="collapse" 
                data-bs-target="#navbarNav">
            <span class="navbar-toggler-icon"></span>
        </button>

        <!-- Menu Navigasi -->
        <div class="collapse navbar-collapse" id="navbarNav">
            <ul class="navbar-nav ms-auto">
                <li class="nav-item">
                    <a class="nav-link" href="#home">Home</a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#about">About</a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#documentation">Dokumentasi</a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#certificates">Certificates</a>
                </li>
            </ul>
        </div>

    </div>
</nav>

a. navbar-expand-lg : Navbar akan collapse saat layar kecil.

b. navbar-dark : Warna teks terang.

c. fixed-top : Navbar selalu di atas saat scroll.

d. ms-auto : Menu rata kanan.

e. data-bs-toggle="collapse" : Mengaktifkan fitur toggle Bootstrap.


2. HERO / HOME SECTION

<section id="home" 
         class="hero d-flex align-items-center text-center text-white">

    <div class="container">

        <!-- Foto Profil -->
        <img src="images/me.jpeg" 
             class="profile-img mb-4" 
             alt="Profile">

        <h1 class="fw-bold">
            {{ name }}
        </h1>

        <!-- Tagline -->
        <p class="lead">
            {{ tagline }}
        </p>

        <a href="#about" 
           class="btn btn-light mt-3">
            Scroll Down
        </a>

    </div>
</section>

d-flex align-items-center : Konten berada di tengah vertikal.

text-center : Teks rata tengah.

{{ name }} : Data binding dari Vue JS.

btn btn-light : Styling tombol Bootstrap.


3. ABOUT SECTION
   
   <section id="about" class="py-5">
    <div class="container">
        <h2 class="text-center mb-5 fw-bold">
            About Me
        </h2>

        <div class="row">

            <!-- Kolom Kiri -->
            <div class="col-md-6">
                <p>{{ about }}</p>

                <h5 class="mt-4">Pengalaman</h5>
                <ul>
                    <li v-for="exp in experiences">
                        {{ exp }}
                    </li>
                </ul>
            </div>

            <!-- Kolom Kanan -->
            <div class="col-md-6">
                <h5>Skill Level</h5>

                <div v-for="skill in skills" 
                     class="mb-3">

                    <label>
                        {{ skill.name }}
                    </label>

                    <div class="progress">
                        <div class="progress-bar"
                             :style="{ width: skill.level + '%' }">
                            {{ skill.level }}%
                        </div>
                    </div>

                </div>

            </div>
        </div>
    </div>
</section>

a. Digunakan untuk menampilkan data array

experiences: [
    "Kepanitiaan Aplikasi",
    "Panitia Insevent",
    "Pengurus Organisasi Kampus"
]

b. Progress Bar Dinamis

<div class="progress-bar"
     :style="{ width: skill.level + '%' }">

:style → Binding style secara dinamis.

Lebar progress mengikuti nilai skill.level.


4. DOKUMENTASI SECTION

   <section id="documentation" class="py-5 bg-light">
    <div class="container">
        <h2 class="text-center mb-5 fw-bold">
            Dokumentasi Kegiatan
        </h2>

        <div class="row text-center">

            <div class="col-md-4 mb-4">
                <div class="card shadow h-100">

                    <img src="images/ap.JPEG" 
                         class="card-img-top" 
                         alt="Dokumentasi">

                    <div class="card-body">
                        <p class="card-text">
                            Kepanitiaan Aplikasi
                        </p>
                    </div>

                </div>
            </div>

        </div>
    </div>
</section>

col-md-4 : 3 kolom per baris.

card shadow : Komponen kartu Bootstrap.

h-100 : Tinggi card sama rata.


5. CERTIFICATES SECTION

   <section id="certificates" class="py-5">
    <div class="container">
        <h2 class="text-center mb-5 fw-bold">
            Certificates
        </h2>

        <div class="row">

            <div class="col-md-3 mb-4"
                 v-for="cert in certificates">

                <div class="card shadow-sm h-100">

                    <img :src="cert.image"
                         class="card-img-top"
                         alt="Certificate">

                    <div class="card-body">
                        <h6>{{ cert.title }}</h6>
                        <p class="small">
                            {{ cert.description }}
                        </p>
                    </div>

                </div>
            </div>

        </div>
    </div>
</section>

v-for="cert in certificates" : Loop data sertifikat.

:src="cert.image" : Binding gambar secara dinamis.

Setiap card dibuat otomatis sesuai jumlah data di array.


6. FOOTER

   <footer class="custom-footer text-center">
    <div class="container">
        <p>
            © 2026 - {{ name }} | Portfolio Website
        </p>
    </div>
</footer>

custom-footer : Styling dari CSS.

text-center : Teks rata tengah.

{{ name }} : Data dinamis dari Vue.


7. VUE JS (LOGIC UTAMA)

   <script>
const { createApp } = Vue

createApp({
    data() {
        return {

            name: "Elvira Agustin",
            tagline: "Mahasiswa",

            about: "Saya mampu memanajemen waktu dan bekerja dalam tim.",

            experiences: [
                "Kepanitiaan Aplikasi",
                "Panitia Insevent",
                "Pengurus Organisasi Kampus"
            ],

            skills: [
                { name: "Manajemen Waktu", level: 90 },
                { name: "Kerjasama Tim", level: 85 },
                { name: "Komunikasi", level: 75 }
            ],

            certificates: [
                {
                    title: "Kepanitiaan Aplikasi",
                    description: "Pengalaman organisasi.",
                    image: "images/aplikasi.jpeg"
                }
            ]

        }
    }
}).mount('#app')
</script>

createApp() : Membuat aplikasi Vue.

data() : Menyimpan semua data.

.mount('#app') : Menghubungkan Vue dengan HTML id="app".


## Ringkasan Teknologi

| Teknologi   | Fungsi                          |
| ----------- | ------------------------------- |
| HTML5       | Struktur website                |
| CSS3        | Styling & desain                |
| Bootstrap 5 | Layout responsive & komponen UI |
| Vue JS 3    | Data dinamis & interaktif       |
| JavaScript  | Logika program                  |


## TAMPILAN

<img width="1919" height="873" alt="image" src="https://github.com/user-attachments/assets/57c2382a-0526-44b3-927f-e0da1d902f88" />

<img width="1919" height="875" alt="image" src="https://github.com/user-attachments/assets/c9dba3bb-e585-4e0e-b998-992e1f9bd925" />

<img width="1918" height="868" alt="image" src="https://github.com/user-attachments/assets/1381d91f-9520-4640-b18a-03c00c65ce4a" />

<img width="1919" height="875" alt="image" src="https://github.com/user-attachments/assets/c34cc373-b4d2-4f8b-952c-70253fae6a64" />
   
