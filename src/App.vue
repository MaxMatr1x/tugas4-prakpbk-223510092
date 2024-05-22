<template>
  <div id="app">
    <div class="header">
      <h1>Selamat Datang di Resto</h1>
      <h2>{{ menupilih }}</h2>
    </div>
    <div class="menu-buttons">
      <button @click="tampilkanMenu('makanan')">Menu Makanan</button>
      <button @click="tampilkanMenu('minuman')">Menu Minuman</button>
    </div>
    <Makanan 
      v-if="menuTerpilih === 'makanan'" 
      :menuMakanan="menuMakanan" 
      @tampilkan-detail="tampilkanDetailMakanan" 
      :makananTerpilih="makananTerpilih" 
      :menampilkanDetail="menampilkanDetail" 
    />
    <Minuman 
      v-if="menuTerpilih === 'minuman'" 
      :menuMinuman="menuMinuman" 
      @tampilkan-detail="tampilkanDetailMinuman" 
      :minumanTerpilih="minumanTerpilih" 
      :menampilkanDetail="menampilkanDetail" 
    />
    <div v-if="menampilkanDetail" class="detail-box">
      <h3>Detail Menu</h3>
      <p>Nama: {{ menuTerpilih === 'makanan' ? makananTerpilih.nama : minumanTerpilih.nama }}</p>
      <p>Harga: Rp{{ menuTerpilih === 'makanan' ? makananTerpilih.harga : minumanTerpilih.harga }}</p>
      <p>Deskripsi: {{ menuTerpilih === 'makanan' ? makananTerpilih.deskripsi : minumanTerpilih.deskripsi }}</p>
    </div>
    <SlotContent ref="slotContentRef" />
  </div>
</template>

<script setup>
import { ref } from 'vue';
import Makanan from './components/Makanan.vue';
import Minuman from './components/Minuman.vue';
import SlotContent from './components/SlotContent.vue';

const menupilih = ref("Pilih Menu Yang Anda Mau : ");
const menuTerpilih = ref(null);
const menampilkanDetail = ref(false);
const makananTerpilih = ref(null);
const minumanTerpilih = ref(null);

const menuMakanan = [
  { nama: "Burger", harga: 50000, deskripsi: "Burger sapi lezat dengan sayuran segar." },
  { nama: "Pizza", harga: 70000, deskripsi: "Pizza enak dengan berbagai topping." },
  { nama: "Pasta", harga: 60000, deskripsi: "Hidangan pasta klasik dengan saus buatan sendiri." }
];

const menuMinuman = [
  { nama: "Cola", harga: 10000, deskripsi: "Minuman cola yang menyegarkan." },
  { nama: "Jus Jeruk", harga: 15000, deskripsi: "Jus jeruk segar yang diperas langsung." },
  { nama: "Teh Es", harga: 12000, deskripsi: "Teh es dingin dengan lemon." }
];

function tampilkanMenu(menu) {
  menuTerpilih.value = menu;
  menampilkanDetail.value = false;
  makananTerpilih.value = null;
  minumanTerpilih.value = null;
}

function tampilkanDetailMakanan(makanan) {
  makananTerpilih.value = makanan;
  menampilkanDetail.value = true;
}

function tampilkanDetailMinuman(minuman) {
  minumanTerpilih.value = minuman;
  menampilkanDetail.value = true;
}

function updateSlotContent(newContent) {
  this.$refs.slotContentRef.slotContent = newContent;
}
</script>

<style scoped>
#app {
  font-family: Arial, sans-serif;
  text-align: center;
  margin-top: 50px;
  background-image: url('/src/assets/latar.jpg');
  background-size: cover;
  background-position: center;
  height: 100%;
}

.header {
  padding: 20px;
  margin-bottom: 20px;
  border-radius: 5px;
}

.menu-buttons {
  margin-bottom: 20px;
}

h1 {
  color: #fafafa;
}

h2 {
  color: #a1a0a0;
}

button {
  background-color: #4CAF50;
  color: white;
  padding: 10px 20px;
  font-size: 16px;
  border: none;
  cursor: pointer;
  border-radius: 5px;
  margin: 10px;
}

button:hover {
  background-color: #45a049;
}

.detail-box {
  padding: 20px;
  margin-top: 20px;
  border-radius: 5px;
}
</style>
