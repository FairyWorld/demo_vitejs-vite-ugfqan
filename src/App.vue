<!-- html模板 -->
<template>
  <div class="container">
    <h1>待办列表</h1>
    <input type="text" v-model="newTodo" placeholder="输入待办事项" />
    <button @click="addTodo">添加</button>
    <ul>
      <li v-for="(todo, index) in todos" :key="index">
        {{ todo }}
      </li>
    </ul>
  </div>
  <HelloWorld />
</template>

<!-- 业务逻辑 -->
<script setup>
import { ref } from 'vue';
import HelloWorld from './components/HelloWorld.vue';

const newTodo = ref(''); // 响应式变量newTodo，表示输入框的值
const todos = ref([]); // 响应式变量todos，表示待办列表

const addTodo = () => {
  if (newTodo.value) {
    todos.value.push(newTodo.value); // 将输入的值添加到列表中
    newTodo.value = ''; // 清空输入框的值
  }
};
</script>

<!-- 样式 -->
<style scoped>
.container {
  max-width: 400px;
  margin: 0 auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
  background-color: #f8f8f8;
}

h1 {
  font-size: 24px;
  margin-bottom: 10px;
}

input {
  padding: 5px 10px;
  margin-right: 10px;
  border: 1px solid #ddd;
  border-radius: 3px;
  font-size: 14px;
}

button {
  padding: 5px 10px;
  background-color: #4caf50;
  color: #fff;
  border: none;
  border-radius: 3px;
  font-size: 14px;
  cursor: pointer;
}

ul {
  list-style-type: none;
  padding: 0;
  margin: 10px 0;
  text-align: left;
}

li {
  margin-bottom: 10px;
}
</style>
