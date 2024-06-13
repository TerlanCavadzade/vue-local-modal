<script setup lang="ts"></script>

<template>
  <div class="modal">
    <div class="bg"></div>
    <div class="content"><slot /></div>
  </div>
</template>

<style scoped>
.modal {
  position: fixed;
  inset: 0;
}

.bg {
  position: absolute;
  inset: 0;
  background-color: rgba(0, 0, 0, 0.1);
}
</style>
