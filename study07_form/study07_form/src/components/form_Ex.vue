<script setup>
import { ref } from "vue";

const favoriteColor = ref("");

const agree = ref(false);

const selectedFruits = ref([]);

const selectedCity = ref("");
// 다중 선택을 처리하고 있으므로, selectedHobbies는 배열이어야 한다.
const selectedHobbies = ref([]);
</script>

<template>
  <!-- 단일선택 하는 방법 (*radio는 다중선택 불가!) -->
  <div class="radio-group">
    <p>🧜🏼‍♀️좋아하는 색깔은?</p>
    <label class="radio">
      <input type="radio" v-model="favoriteColor" value="빨강" />
      <span class="custom-radio"></span>
      빨강
    </label>
    <label class="radio">
      <input type="radio" v-model="favoriteColor" value="파랑" />
      <span class="custom-radio"></span>
      파랑
    </label>
    <label class="radio">
      <input type="radio" v-model="favoriteColor" value="초록" />
      <span class="custom-radio"> </span>
      초록
    </label>
    <p>
      ✅ 선택한 색상: <strong> {{ favoriteColor }} </strong>
    </p>
  </div>
  <div class="radio-group">
    <!-- 예제 1: 단일 체크박스(불리언 값) -->
    <h2>예제 1: 단일 체크박스(불리언 값)</h2>
    <label>
      <input type="checkbox" v-model="agree" />
      약관에 동의합니다.
    </label>
    <p>동의 여부: {{ agree }}</p>

    <!-- 예제 2: 여러 체크박스(배열에 저장) -->
    <h2>예제 2: 여러 체크박스(배열에 저장)</h2>
    <div class="checkbox-group">
      <p>🐥 좋아하는 과일을 선택하세요:</p>
      <label class="checkbox-label">
        <input type="checkbox" v-model="selectedFruits" value="apple" />
        <span class="custom-checkbox"></span>
        🍎apple
      </label>
      <label class="checkbox-label">
        <input type="checkbox" v-model="selectedFruits" value="banana" />
        <span class="custom-checkbox"></span>
        🍌banana
      </label>
      <label class="checkbox-label">
        <input type="checkbox" v-model="selectedFruits" value="cherry" />
        <span class="custom-checkbox"></span>
        🍒cherry
      </label>
      <p>
        ✅선택한 과일은 <strong>{{ selectedFruits }}</strong
        >입니다⭐
      </p>
    </div>
  </div>
  <div class="radio-group">
    <!-- 셀렉트 박스값 바인딩 -->
    <h1>🎈셀렉트 박스값 바인딩🎈</h1>
    <!-- 예제 1: 단일 선택 -->
    <h2>예제 1: 단일 선택</h2>
    <div class="select-group">
      <p>도시를 선택하세요🎠</p>
      <select v-model="selectedCity" class="custom-select">
        <option value="" selected disabled>도시를 선택하쇼!</option>
        <option value="서울">Seoul</option>
        <option value="부산">Busan</option>
        <option value="대구">Daegu</option>
      </select>
      <p>
        ✅선택한 도시는 <strong>{{ selectedCity }}</strong
        >입니다⭐
      </p>
    </div>
    <!-- 예제 2: 다중 선택 -->
    <h2>예제 2: 다중 선택 (배열로 저장)</h2>
    <p>취미를 선택하세요 (Ctrl 또는 Shift 키를 누르고 여러 개 선택 가능)</p>
    <select v-model="selectedHobbies" class="custom-select" multiple>
      <option value="독서">독서</option>
      <option value="운동">운동</option>
      <option value="게임">게임</option>
      <option value="여행">여행</option>
    </select>
    <p>✅선택한 취미는 {{ selectedHobbies }}입니다⭐</p>
  </div>
</template>

<style scoped>
h2 {
  margin: 10px 0;
}
.radio-group {
  width: 40%;
  padding: 6px;
  margin: 20px;
  border-radius: 5px;
  border: 2px solid #8bc266;
}
.radio,
.checkbox-label {
  display: flex;
  align-items: center;
  gap: 8px;
  cursor: pointer;
  font-size: 16px;
  margin: 5px 0;
}
.radio input,
.checkbox-label input {
  display: none;
}
.custom-radio,
.custom-checkbox {
  width: 13px;
  height: 13px;
  border: 2px solid palevioletred;
  border-radius: 20%;
  display: inline-block;
  position: relative;
}
.radio input:checked + .custom-radio,
.checkbox-label input:checked + .custom-checkbox {
  border: palevioletred;
  background-color: palevioletred;
  position: relative;
}
.checkbox-label input:checked + .custom-checkbox::after {
  content: "✔";
  color: #971313;
  position: absolute;
  top: -6px;
  left: 1px;
}
.custom-select {
  margin: 8px 0;
  padding: 6px;
  font-size: 15px;
  border: 2px solid gray;
  border-radius: 5px;
  background-color: #fff;
  cursor: pointer;
  transition: all 0.3s;
}
.custom-select:focus {
  border-color: green;
  outline: none;
  box-shadow: 0 0 5px rgba(0, 0, 0, 0.2);
}
</style>
