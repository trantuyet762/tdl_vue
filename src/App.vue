<script setup>
import TodoList from './components/TodoList.vue'
</script>

<template>
  <div class="app">
    <TodoList />
  </div>
</template>

<style>
.app {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  background: linear-gradient(135deg, #6dd5ed 0%, #2193b0 100%);
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

body {
  margin: 0;
  padding: 0;
  background-color: #f5f5f5;
}
</style> 