<template>
    <div>
      <p>{{ slotContent }}</p>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  const slotContent = ref("Kami tidak pernah meragukan tamu, meski permintaannya aneh-aneh");
  </script>
  
  <style scoped>

  </style>
