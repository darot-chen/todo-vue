<script setup>
import { ref } from "vue"
import Navbar from "./components/Navbar.vue";
import TodoForm from "./components/TodoForm.vue";
import TodoItem from "./components/TodoItem.vue";
</script>

<template>
  <Navbar />
  <TodoForm />
  <!-- <TodoItem /> -->
</template>

<style>
body {
  @apply bg-gray-400;
  @apply font-sans;
  @apply text-white;
}
</style>
