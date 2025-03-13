<script setup>
import { ref } from "vue";
// 할 일 목록 데이터(더미데이터)
const todos = ref([
  { id: 1, name: "Vue 공부하기", isComplete: false },
  { id: 2, name: "운동하기", isComplete: true },
  { id: 3, name: "책 읽기", isComplete: false },
]);
// 할 일 추가
const newTodo = ref("");
console.log(todos);

const addTodo = () => {
  if (newTodo.value.trim()) {
    todos.value.push({ id: Date.now(), name: newTodo.value, isComplete: false });
    newTodo.value = ""; // 입력필드 초기화
  }
  console.log(todos);
};
// 할 일 완료 & 미완료 토글
const toggleComplete = (todo) => {
  todo.isComplete = !todo.isComplete; // 반대되는 것!(토글기능)
};
// 완료된 항목 삭제 기능
const deleteCompleted = () => {
  todos.value = todos.value.filter((todo) => !todo.isComplete);
};
</script>
<template>
  <div class="todo-wrap">
    <h1>💟 Todo List</h1>
    <!-- 할 일 입력 -->
    <div class="input-group">
      <input v-model="newTodo" placeholder="새로운 할 일 목록 입력!" />
      <button @click="addTodo">추가</button>
    </div>
    <h2>📌진행 중</h2>
    <ul>
      <template v-for="todo in todos" :key="todo.id">
        <li v-if="!todo.isComplete">
          <input type="checkbox" @change="toggleComplete(todo)" />
          {{ todo.name }}
        </li>
      </template>
    </ul>
    <!-- 완료된 할 일 목록 -->
    <h2>✅완료</h2>
    <ul>
      <template v-for="todo in todos" :key="todo.id">
        <li v-if="todo.isComplete">
          <input type="checkbox" checked @change="toggleComplete(todo)" />
          {{ todo.name }}
        </li>
      </template>
    </ul>
    <!-- 완료된 목록 삭제 버튼 -->
    <button @click="deleteCompleted" class="delete-btn">완료된 항목 삭제🪓</button>
  </div>
</template>
<style scoped>
.todo-wrap {
  display: flex;
  flex-direction: column;
  width: 300px;
  margin: auto;
  padding: 30px;
}
.input-group {
  display: flex;
  justify-content: space-around;
  margin: 10px 0;
}
button {
  padding: 5px 10px;
  cursor: pointer;
}
ul {
  list-style: none;
  padding: 0;
}
li {
  display: flex;
  align-items: center;
  gap: 5px;
  margin: 6px 0;
}
h2{
    margin-top: 15px;
    text-align: left;
}
.delete-btn {
  margin-top: 10px;
  background: rgb(74, 184, 41);
  color: white;
  border: none;
  padding: 5px 10px;
}
</style>
