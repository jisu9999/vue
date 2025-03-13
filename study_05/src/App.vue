<script setup>
import { ref } from "vue";
import ExArr from "./ExArr.vue";
import Event from "./Event.vue";
const showEventEx = ref(false);
</script>

<template>
  <ExArr />
  <hr />
  <div class="event-wrap">
    <button @click="showEventEx = !showEventEx" class="showEvent-btn">
      {{ showEventEx ? "닫기❎" : "Event 예제 보기🎈" }}
    </button>
    <Event v-if="showEventEx" />
  </div>
</template>

<style scoped>
.showEvent-btn {
  display: block;
  margin: auto;
  margin-top: 10px;
  cursor: pointer;
}
</style>
