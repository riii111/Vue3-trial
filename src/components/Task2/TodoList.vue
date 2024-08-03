<template>
  <div>
    <h2>Todoリスト</h2>
    <a>TODOアイテムを追加しよう</a>
    <form @submit.prevent="addTodo" class="todo-add">
      <input v-model.trim="newTodo" />
      <button>追加！</button>
    </form>

    <ul class="todo-list">
      <li v-for="todo in todoList" :key="todo.id" class="todo-item">
        <input type="checkbox" v-model="todo.completed" />
        <span :class="{ completed: todo.completed }">{{ todo.text }}</span>
        <button @click="removeTodo(todo)" class="delete-btn">削除</button>
      </li>
    </ul>
  </div>
</template>

<script setup>
/*
お題：
基本的なTodoリストアプリケーションを作成してください。以下の機能を実装してください：

- 新しいTodoアイテムを追加できる入力フィールド
- Todoアイテムのリストを表示する
- 各Todoアイテムに対して、完了/未完了の切り替えができるチェックボックス
- 完了したTodoアイテムに取り消し線を表示する
- Todoアイテムを削除するボタン
 */

import { ref, reactive } from "vue";

let id = 0;

const newTodo = ref("");
const todoList = reactive([
  { id: id++, text: "Hello Vue3", completed: true },
  { id: id++, text: "Hello Nuxt3", completed: false },
  { id: id++, text: "I'm very interested in Rust", completed: false },
]);

const addTodo = () => {
  if (newTodo.value) {
    todoList.push({
      id: id++,
      text: newTodo.value,
      completed: false,
    });
    newTodo.value = "";
  }
};

const removeTodo = (todo) => {
  const index = todoList.findIndex((item) => todo.id === item.id);
  if (index !== -1) todoList.splice(index, 1);
};
</script>

<style scoped>
.todo-add {
  display: flex;
  justify-content: center;
  gap: 10px;
  margin-bottom: 20px;
}

.todo-list {
  list-style-type: none; /* リスト項目のマーカー */
  padding: 0;
}

.todo-item {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 10px;
}

button {
  padding: 5px 10px;
  background-color: #4caf50;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover:not(:disabled) {
  background-color: #45a049;
}

button:disabled {
  background-color: #cccccc;
  cursor: not-allowed;
}

.completed {
  text-decoration: line-through;
  color: #888;
}

.delete-btn {
  background-color: #f44336;
}

.delete-btn:hover {
  background-color: #d32f2f;
}
</style>
