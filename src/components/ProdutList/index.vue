<script setup lang="ts">
import { ref } from "vue";
import { Product } from "../../types/product";
import Modal from "../Modal/index.vue";

defineProps<{ products: Product[] }>();
const modalData = ref<Product | null>(null);

const modalOpenHandler = (product: Product) => {
  modalData.value = product;
};
</script>

<template>
  <ul>
    <li v-for="product in $props.products" :key="product.id">
      <div class="img">
        <img :src="product.thumbnail" :alt="product.title" />
      </div>
      <p>
        {{ product.title }}
      </p>
      <button @click="modalOpenHandler(product)">Details</button>
    </li>
  </ul>

  <Modal v-show="modalData">
    <h2>{{ modalData?.title }}</h2>
  </Modal>
</template>

<style scoped>
ul {
  list-style: none;
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(min(100%, 330px), 1fr));
  gap: 15px;
}
</style>
