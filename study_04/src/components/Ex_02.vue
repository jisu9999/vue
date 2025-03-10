<script setup>
import { computed, reactive, ref } from "vue";

// 예약 카운트 증가 및 두배 표시 기능
const reservation = ref(0);
const dbreservation = computed(() => {
  return reservation.value * 2; // {}객체 안에 적을때는 return 필수!
});
const increaseReservation = () => {
  reservation.value++;
};
// 짐 보관 상태
const storage = reactive({
  isStored: false,
});
// 토글 버튼에 대한 기능
const toggleStorage = () => {
  storage.isStored = !storage.isStored;
};
// 3.제빙기 청소 옵션 선택 및 요금 계산
const selectiedOption = ref("basic");
const totalPrice = computed(() => (selectiedOption.value === "basic" ? 50000 : 100000));
// 4.고객 정보 관리 및 업데이트
const customer = reactive({
  name: "김할리",
  phone: "010-0630-0909",
});
const updateCustomer = () => {
  customer.name = "김태현";
  customer.phone = "010-1009-0909";
};
// 5.남은 예약 가능 수 계산
const maxReservation = ref(10); // 최대 예약 가능 수
const currentReservation = ref(0); // 현재 예약 수
const remainReservations = computed(() => maxReservation.value - currentReservation.value); // 남은 예약 가능 수
const addReservetion = () => {
  if (currentReservation.value < maxReservation.value) {
    currentReservation.value++;
  }
};
</script>
<template>
  <div class="wrap">
    <!-- 예약 카운트 증가 및 두배 표시 -->
    <div class="ex">
      <h2>예약 관리</h2>
      <p>예약 수: {{ reservation }}</p>
      <p>두배 예약 수: {{ dbreservation }}</p>
      <button @click="increaseReservation">예약 추가</button>
    </div>
    <hr />
    <div class="ex">
      <!-- 짐 보관 상태 -->
      <h2>짐 보관 상태</h2>
      <p>짐 보관 상태: {{ storage.isStored ? "보관중" : "미보관" }}</p>
      <button @click="toggleStorage">짐보관 토글</button>
    </div>
    <hr />
    <div class="ex">
      <!-- 3.제빙기 청소 옵션 선택 및 요금 계산 -->
      <h2>🧊제빙기 청소 예약🛴</h2>
      <label>
        청소 옵션:
        <select v-model="selectiedOption">
          <option value="basic">기본 청소 (₩50,000)</option>
          <option value="deep">심층 청소 (₩100,000)</option>
        </select>
      </label>
      <p>선택한 요금: {{ totalPrice }}</p>
    </div>
    <hr />
    <!-- 4.고객 정보 관리 및 업데이트 -->
    <div class="ex">
      <h2>고객 정보</h2>
      <p>고객 이름 : {{ customer.name }}</p>
      <p>전화번호 : {{ customer.phone }}</p>
      <button @click="updateCustomer">정보 변경</button>
    </div>
    <hr />
    <!-- 5.남은 예약 가능 수 계산 -->
    <div class="ex">
      <h2>예약 가능 여부</h2>
      <p>최대 예약 가능 수: {{ maxReservation }}</p>
      <p>현재 예약 수: {{ currentReservation }}</p>
      <p>남은 예약 가능 수: {{ remainReservations }}</p>
      <button @click="addReservetion" :disabled="currentReservation >= maxReservation">예약 추가</button>
    </div>
  </div>
</template>
<style scoped>
.wrap {
  display: flex;
  gap: 20px;
}
.ex {
  flex: 1;
}
button {
  margin: 5px;
  padding: 8px 12px;
  border: none;
  background-color: #42b983;
  color: white;
  cursor: pointer;
  border-radius: 5px;
}
button.disabled {
  background-color: gray;
  cursor: not-allowed;
}
</style>
