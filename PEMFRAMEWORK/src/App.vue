<script setup>
import { ref } from 'vue'; // Tambahkan ref untuk reactive data

const count = ref(0); // Inisialisasi counter
const boxColor = ref('lightblue'); // Inisialisasi warna kotak

// Inisialisasi daftar gambar untuk carousel
const images = [
  'https://e0.pxfuel.com/wallpapers/434/478/desktop-wallpaper-site-site-anime-background-pemandangan-anime.jpg', // Gambar pertama
  'https://p4.wallpaperbetter.com/wallpaper/601/786/348/anime-street-scenic-buildings-bicycle-wallpaper-preview.jpg', // Gambar kedua
  'https://e1.pxfuel.com/desktop-wallpaper/416/519/desktop-wallpaper-anime-scenery-city-fresh-13-wonderful-anime-city-this-year-anime-street-scenery.jpg'  // Gambar ketiga
];

const currentImageIndex = ref(0); // Indeks gambar yang sedang ditampilkan

function increment() {
  count.value++; // Fungsi untuk menambah counter
}

function changeColor() {
  // Fungsi untuk mengubah warna kotak
  const colors = ['lightblue', 'lightcoral', 'lightgreen', 'lightgoldenrodyellow', 'lightpink'];
  boxColor.value = colors[Math.floor(Math.random() * colors.length)];
}

function nextImage() {
  // Fungsi untuk pindah ke gambar berikutnya
  currentImageIndex.value = (currentImageIndex.value + 1) % images.length;
}

function prevImage() {
  // Fungsi untuk kembali ke gambar sebelumnya
  currentImageIndex.value = (currentImageIndex.value - 1 + images.length) % images.length;
}
</script>

<template>
  <div>
    <p>Counter: {{ count }}</p>

    <div :style="{ backgroundColor: boxColor, width: '100px', height: '100px', margin: '20px auto' }"></div>
    <button @click="changeColor" class="futuristic-button">Touch me!</button> <!-- Tombol untuk mengubah warna kotak -->

    <!-- Carousel gambar -->
    <div class="carousel">
      <button @click="prevImage" class="futuristic-button">Previous</button>
      <img :src="images[currentImageIndex]" alt="Carousel Image" class="carousel-image" />
      <button @click="nextImage" class="futuristic-button">Next</button>
    </div>
  </div>
</template>

<style scoped>
/* Tambahkan gaya sesuai kebutuhan */
div {
  text-align: center;
  margin-top: 2rem;
}

.futuristic-button {
  padding: 0.8rem 1.5rem;
  font-size: 1.2rem;
  border: none;
  border-radius: 8px;
  background: linear-gradient(45deg, #6a11cb, #2575fc);
  color: white;
  cursor: pointer;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  transition: all 0.3s ease;
}

.futuristic-button:hover {
  background: linear-gradient(45deg, #2575fc, #6a11cb);
  transform: translateY(-2px);
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.3);
}

.futuristic-button:active {
  transform: translateY(1px);
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
}

.carousel {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-top: 20px;
}

.carousel button {
  padding: 0.8rem;
  margin: 0 10px;
  border-radius: 8px;
}

.carousel-image {
  display: block;
  margin: 20px auto;
  width: 300px; /* Ukuran gambar diperbesar */
  height: auto;
}
</style>
