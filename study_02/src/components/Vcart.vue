<script setup>
import { ref } from "vue";
const products = ["🍕PIZZA", "🍰CAKE", "🍔HAMBURGER"];
const cart = ref([]); // 선택한 상품들이 담기는 곳
const addToCart = (product) => {
  cart.value.push(product);
};
</script>
<template>
  <h2>상품 목록</h2>
  <ul>
    <li v-for="product in products" :key="product">
      {{ product }}
      <button @click="addToCart(product)">➕추가</button>
    </li>
  </ul>
  <h2>🛒장바구니</h2>
  <ul>
    <li v-for="item in cart" :key="item">{{ item }}</li>
  </ul>
</template>
<style scoped></style>
