<template>
  <div class="menu-box">
    <h3>Menu Minuman</h3>
    <div v-for="(minuman, index) in menuMinuman" :key="index" class="menu-item">
      <p>{{ minuman.nama }} - Rp{{ minuman.harga }}</p>
      <button @click="tampilkanDetailMinuman(minuman)">Detail</button>
    </div>
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue';

const props = defineProps({
  minumanTerpilih: Object,
  menampilkanDetail: Boolean
});

const emit = defineEmits(['tampilkan-detail']);

const menuMinuman = [
  { nama: "Cola", harga: 10000, deskripsi: "Minuman cola yang menyegarkan." },
  { nama: "Jus Jeruk", harga: 15000, deskripsi: "Jus jeruk segar yang diperas langsung." },
  { nama: "Teh Es", harga: 12000, deskripsi: "Teh es dingin dengan lemon." }
];

function tampilkanDetailMinuman(minuman) {
  emit('tampilkan-detail', minuman);
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
