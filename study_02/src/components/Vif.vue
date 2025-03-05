<script setup>
import { ref } from "vue";
const show = ref(false);
const show1 = ref(false);
const isVisible = ref(false)
</script>
<template>
  <button @click="show = !show">상세 설명보기</button>
  <p v-if="show">이 상품은 정말 좋아요! 👓</p>
  <br />
  <button @click="show1 = !show1">열려라</button>
  <p v-if="show1">안녕 안녕~👻</p>
  <!-- 설명 숨기기 삼항연산자 -->
  <button @click="isVisible = !isVisible">
  {{ isVisible ? "설명 숨기기" : "설명 보기" }}
  </button>
  <p v-show="isVisible">이제품은 품질이 뛰어나고 인기가 많아유~🤑</p>
</template>
<style scoped></style>
