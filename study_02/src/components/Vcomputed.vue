<script setup>
import { ref, computed } from "vue";
// 사용자가 입력한 검색어를 저장하는 변수
const search = ref("");

const items = ["📱아이폰", "🌠갤럭시", "💻맥북"];
// filteredItems(ccomputed): 사용자가 검색한 검색어(search.value)가
// 포함된 includes()상품만 보여줌
const filteredItems = computed(() => {
  return items.filter((item) => item.includes(search.value));
});
// 상품리스트 표시
const products = ["🍕PIZZA", "🍰CAKE", "🍔HAMBURGER"];
// 상품리스트 표시2
const prds = ["💍ring", "👒hat", "👜bag"];
</script>
<template>
  <h2>검색기능</h2>
  <!-- 사용자가 입력한 검색어를 search변수에 자동으로 반영되는것: v-model -->
  <input v-model="search" placeholder="상품 검색" />
  <ul>
    <!-- v-for 반복문(forEach같은 것!)을 사용해서 filteredItems 배열을 돌며 li태그로 상품을 표시함 -->
    <li v-for="item in filteredItems" :key="item">{{ item }}</li>
  </ul>
  <hr />
  <h2>상품리스트 출력</h2>
  <ul>
    <li v-for="product in products" :key="product">{{ product }}</li>
  </ul>
  <hr />
  <h2>ACC LIST</h2>
  <ul>
    <li v-for="prd in prds" :key="prd">{{ prd }}</li>
  </ul>
</template>
<style scoped></style>
