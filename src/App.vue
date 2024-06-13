<script setup lang="ts">
import { onMounted, reactive } from "vue";
import { Product, ProductRes } from "./types/product";
import ProductList from "./components/ProdutList/index.vue";

const products = reactive<Product[]>([]);

onMounted(async () => {
  const res = await fetch("https://dummyjson.com/products");
  const data: ProductRes = await res.json();
  products.push(...data.products);
});
</script>

<template>
  <ProductList :products="products" />
</template>

<style scoped></style>
