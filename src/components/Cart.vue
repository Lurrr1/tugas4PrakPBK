<template>
  <div>
    <h2>Cart</h2>
    <div v-if="cartItems.length === 0">Your cart is empty</div>
    <div v-else>
      <div v-for="item in cartItems" :key="item.id" class="cart-item">
        <h3>{{ item.name }}</h3>
        <p>Price: ${{ item.price }}</p>
        <p>Quantity: {{ item.quantity }}</p>
        <button @click="removeFromCart(item)">Remove</button>
      </div>
      <h3>Total: ${{ total }}</h3>
    </div>
  </div>
</template>

<script setup>
import { defineProps, defineEmits, computed } from "vue";

const props = defineProps({
  cartItems: Array,
});

const emit = defineEmits(["removeFromCart"]);

const removeFromCart = (product) => {
  emit("removeFromCart", product);
};

const total = computed(() => {
  return props.cartItems.reduce(
    (sum, item) => sum + item.price * item.quantity,
    0
  );
});
</script>

<style scoped>
/* Add your scoped styles here */
.cart-item {
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
