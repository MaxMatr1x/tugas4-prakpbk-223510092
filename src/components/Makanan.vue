<template>
  <div class="menu-box">
    <h3>Menu Makanan</h3>
    <div v-for="(makanan, index) in menuMakanan" :key="index" class="menu-item">
      <p>{{ makanan.nama }} - Rp{{ makanan.harga }}</p>
      <button @click="tampilkanDetailMakanan(makanan)">Detail</button>
    </div>
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue';

const props = defineProps({
  makananTerpilih: Object,
  menampilkanDetail: Boolean
});

const emit = defineEmits(['tampilkan-detail']);

const menuMakanan = [
  { nama: "Burger", harga: 50000, deskripsi: "Burger sapi lezat dengan sayuran segar." },
  { nama: "Pizza", harga: 70000, deskripsi: "Pizza enak dengan berbagai topping." },
  { nama: "Pasta", harga: 60000, deskripsi: "Hidangan pasta klasik dengan saus buatan sendiri." }
];

function tampilkanDetailMakanan(makanan) {
  emit('tampilkan-detail', makanan);
}
</script>

<style scoped>
.menu-box {
  padding: 20px;
  border-radius: 5px;
  margin-bottom: 20px;
}

.menu-item {
  margin: 10px 0;
}

button {
  background-color: #4CAF50;
  color: white;
  padding: 5px 10px;
  border: none;
  cursor: pointer;
  border-radius: 5px;
}

button:hover {
  background-color: #45a049;
}
</style>
