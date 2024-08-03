<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png" />
  <HelloWorld msg="Hello Vue 3 in CodeSandbox!" /> -->
  <Task1 />
  <Task2 />
</template>

<script>
import NumCount from "./components/Task1/NumCount.vue";
import TodoList from "./components/Task2/TodoList.vue";

export default {
  name: "App",
  components: {
    // Task1: NumCount,  // 数を増減させるお題.
    Task2: TodoList, // TODOリストを管理するお題.
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
