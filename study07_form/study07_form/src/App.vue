<script setup>
import { ref } from "vue";
import form_Ex from "./components/form_Ex.vue";
import Reservation from "./components/Reservation.vue";
const currentPage = ref("");
// console.log(currentPage); // 빈 문자열
const showPage = (page) => {
  // alert("클릭")
  // console.log(page);
  currentPage.value = page;
  console.log(currentPage.value);
};
</script>

<template>
  <div>
    <div class="btns">
      <button @click="showPage('form_Ex')">폼 예제</button>
      <button @click="showPage('Reservation')">예약신청</button>
    </div>
    <form_Ex v-if="currentPage === 'form_Ex'" />
    <Reservation v-if="currentPage === 'Reservation'" />
  </div>
</template>

<style scoped>
.btns {
  width: 400px;
  display: flex;
  margin:50px auto;
}
button {
  margin: auto;
  padding: 10px;
  width: 160px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}
button:hover {
  background-color: rgb(9, 105, 207);
}
</style>
