<template>
  <div class="product-item">
    <h3>{{ product.name }}</h3>
    <p>Price: ${{ product.price }}</p>
    <button @click="addToCart">Add to Cart</button>
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from "vue";

const props = defineProps({
  product: Object,
});

const emit = defineEmits(["addToCart"]);

const addToCart = () => {
  emit("addToCart", props.product);
};
</script>

<style scoped>
/* Add your scoped styles here */
.product-item {
  border: 1px solid #ccc;
  padding: 10px;
  margin: 10px;
  text-align: left;
}
button {
  padding: 5px 10px;
  cursor: pointer;
}
</style>
