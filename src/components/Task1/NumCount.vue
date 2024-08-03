<template>
  <div>
    <h2>Counter</h2>
    <p>Current count: {{ number }}</p>
    <div class="button-group">
      <button @click="number++" aria-label="Increment">increment</button>
      <button @click="number--" aria-label="Decrement">decrement</button>
      <button @click="reset" aria-label="Reset">reset</button>
    </div>
  </div>
</template>

<script setup>
/* シンプルなカウンターアプリケーションを作成してください。以下の機能を実装してください：
- 現在のカウント値を表示する
  - カウントを増やすボタン
  - カウントを減らすボタン
  - カウントをリセットするボタン */
import { ref } from "vue";

const number = ref(0);

const reset = () => {
  number.value = 0;
};
</script>

<style scoped>
.button-group {
  display: flex;
  justify-content: center;
  gap: 10px;
  margin-top: 10px;
}

.button:hover {
  background-color: #45a049;
}
</style>
