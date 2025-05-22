<template>
  <div class="todo-card">
    <h2 class="text-center mb-4 font-bold text-[1.5rem]">Todo App</h2>
    <div class="add-todo">
      <input v-model="newTodo" @keyup.enter="addTodo" placeholder="Add your new todo" type="text" />
      <button @click="addTodo" class="add-btn" aria-label="Add todo">
        <span class="plus-icon">+</span>
      </button>
    </div>
    <ul class="todo-list">
      <li v-for="(todo, index) in todos" :key="index">
        <span>{{ todo.text }}</span>
        <button @click="removeTodo(index)" class="delete-btn" aria-label="Delete todo">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="18"
            height="18"
            fill="none"
            viewBox="0 0 24 24"
          >
            <rect width="24" height="24" fill="none" />
            <path
              fill="#fff"
              d="M16 9v10H8V9h8m-1.5-6h-5l-1 1H5v2h14V4h-4.5l-1-1zM18 7H6v12c0 1.1.9 2 2 2h8c1.1 0 2-.9 2-2V7z"
            />
          </svg>
        </button>
      </li>
    </ul>
    <div class="footer-row">
      <span v-if="todos.length > 0"
        >You have {{ todos.length }} pending task<span v-if="todos.length > 1">s</span></span
      >
      <button v-if="todos.length > 0" @click="clearAll" class="clear-btn">Clear All</button>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const newTodo = ref('')
const todos = ref([])

const addTodo = () => {
  if (newTodo.value.trim()) {
    todos.value.push({
      text: newTodo.value,
    })
    newTodo.value = ''
  }
}

const removeTodo = (index) => {
  todos.value.splice(index, 1)
}

const clearAll = () => {
  todos.value = []
}
</script>

<style scoped>
h2 {
  margin: 0 0 18px 0;
  font-size: 1.6rem;
  font-weight: bold;
  text-align: center;
}
.todo-card {
  background: #fff;
  border-radius: 12px;
  box-shadow: 0 4px 24px rgba(0, 0, 0, 0.12);
  max-width: 340px;
  width: 100%;
  margin: 0 auto;
  padding: 32px 24px 20px 24px;
  display: flex;
  flex-direction: column;
  align-items: stretch;
}

.add-todo {
  display: flex;
  margin-bottom: 18px;
}

input[type='text'] {
  flex: 1;
  padding: 10px 12px;
  font-size: 15px;
  border: 1px solid #e0e0e0;
  border-radius: 6px 0 0 6px;
  outline: none;
  background: #f7f7f7;
  transition: border 0.2s;
}
input[type='text']:focus {
  border: 1.5px solid #a259ec;
}

.add-btn {
  background: #a259ec;
  border-radius: 0 6px 6px 0;
  border: none;
  padding: 0 18px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 22px;
  color: #fff;
  cursor: pointer;
  transition: background 0.2s;
}
.add-btn:hover {
  background: #7c3aed;
}
.plus-icon {
  font-size: 22px;
  font-weight: bold;
  line-height: 1;
}

.todo-list {
  list-style: none;
  padding: 0;
  margin: 0 0 16px 0;
}
.todo-list li {
  background: #f7f7f7;
  border-radius: 6px;
  margin-bottom: 10px;
  padding: 10px 12px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  font-size: 15px;
}
.delete-btn {
  background: #ef4444;
  border: none;
  border-radius: 4px;
  padding: 6px 8px;
  display: flex;
  align-items: center;
  cursor: pointer;
  transition: background 0.2s;
}
.delete-btn:hover {
  background: #b91c1c;
}
.footer-row {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-top: 8px;
}
.clear-btn {
  background: #a259ec;
  color: #fff;
  border: none;
  border-radius: 6px;
  padding: 6px 16px;
  font-size: 14px;
  cursor: pointer;
  transition: background 0.2s;
}
.clear-btn:hover {
  background: #7c3aed;
}
</style>
