<template>
  <div id="app">
    <h1>VueShop</h1>
    <ProductList :products="products" @addToCart="addToCart" />
    <Cart :cartItems="cart" @removeFromCart="removeFromCart" />
  </div>
</template>

<script setup>
import { ref } from "vue";
import ProductList from "./components/ProductList.vue";
import Cart from "./components/Cart.vue";

const products = ref([
  { id: 1, name: "Product 1", price: 10 },
  { id: 2, name: "Product 2", price: 20 },
  { id: 3, name: "Product 3", price: 30 },
]);

const cart = ref([]);

const addToCart = (product) => {
  const cartItem = cart.value.find((item) => item.id === product.id);
  if (cartItem) {
    cartItem.quantity++;
  } else {
    cart.value.push({ ...product, quantity: 1 });
  }
};

const removeFromCart = (product) => {
  const cartItem = cart.value.find((item) => item.id === product.id);
  if (cartItem.quantity > 1) {
    cartItem.quantity--;
  } else {
    cart.value = cart.value.filter((item) => item.id !== product.id);
  }
};
</script>

<style>
/* Add your global styles here */
#app {
  justify-content: center;
  text-align: center;
  font-family: Arial, sans-serif;
  margin-top: 50px;
}
</style>
