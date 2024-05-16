<template>
  <div>
    <h2>Products</h2>
    <div v-for="product in products" :key="product.id">
      <ProductItem :product="product" @addToCart="addToCart" />
    </div>
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from "vue";
import ProductItem from "./ProductItem.vue";

const props = defineProps({
  products: Array,
});

const emit = defineEmits(["addToCart"]);

const addToCart = (product) => {
  emit("addToCart", product);
};
</script>

<style scoped>
/* Add your scoped styles here */
</style>
