<script setup>
import { ref } from "vue"
const message = ref("My Todo App")
const todo = ref('')
const todoList = ref([])
const completedList = ref([])
const selectedList = ref([])

function addTodo() {
  todoList.value.push(todo.value)
  todo.value = ''
}

function markComplete() {
  console.log(selectedList.value)
  selectedList.value.map(item => {
    completedList.value.push(item)
    todoList.value = todoList.value.filter(todoItem => todoItem != item)
  })
  selectedList.value = [];
}

function deleteTodo() {
  selectedList.value.map(item => {
    completedList.value = completedList.value.filter(completedItem => completedItem != item)
    todoList.value = todoList.value.filter(todoItem => todoItem != item)
  })
}
</script>

<template>
  <div class="container">
    <h1>{{ message }}</h1>
    <div>
      <input type="text" id="todo" placeholder="What is your todo" v-model="todo" @keyup.enter="addTodo">
      <ul>
        <li v-for="item of todoList">
          <input type="checkbox" v-model="selectedList" :id=item :value=item>{{ item }}
        </li>
      </ul>
    </div>
    <div>
      <p v-show="completedList.length">Your completed todo list</p>
      <ul>
        <li v-for=" item  in  completedList " class="completed">
          <input type="checkbox" v-model="selectedList" :id=item :value=item>{{ item }}
        </li>
      </ul>
    </div>
    <button v-show="selectedList.length" @click="markComplete">Mark Complete</button>
    <button v-show="selectedList.length" @click="deleteTodo">Delete</button>
  </div>
</template>

<style>
body {
  background-color: black;
  color: white;
}

.container {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-content: center;
  align-items: center;
  justify-content: center;
}

.completed {
  text-decoration: line-through;
}
</style>