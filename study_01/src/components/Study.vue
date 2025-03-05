<script setup>
import { ref } from "vue";
const message = ref("안녕! 나는 vue! 만나서 반가워 :)");
const myMessage = ref("👧🏻: 그래 안녕! 나는 지수! 🧜🏻‍♀️✨💍🧸")
const count = ref(0)
</script>
<template>
    <h1>{{ message }}</h1>
  <span>{{ message }}</span>
  <h1 class="my">{{ myMessage }}</h1>
  <button @click="count++">눌러봥 {{ count }}</button>
  <button @click="count--">눌러봥 {{ count }}</button>
</template>
<style scoped>
h1{
  color: palevioletred;
  font-family:  Calibri, 'Trebuchet MS', sans-serif;
}
.my{
  color: rgb(81, 166, 236);
  background-color: rgb(248, 255, 150);
  width: 560px;
  text-align: center;
  margin-top: 10px;
}
button{
  margin-right: 10px;
}
</style>