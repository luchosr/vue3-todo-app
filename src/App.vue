<template>
<h1>Vue todo-app</h1>
<form action="" @submit.prevent="addNewTodo">
  <label for="">New Todo</label>
  <input v-model="newTodo" type="text" name="newTodo">
  <button>Add New Todo</button>
</form>
<div class="">
  <ul>
    <li v-for="todo in todos" :key="todo.id">{{todo.content}}</li>
  </ul>
</div>
</template>

<script>

import {ref} from 'vue'

export default {
setup(){
  const newTodo = ref('');
  const todos = ref([]);

  function addNewTodo(){
    todos.value.push({
      id: Date.now(),
      done:false,
      content: newTodo.value,
    })
  }
  return{
    todos,
    newTodo,
    addNewTodo
  }
}
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 0 auto;
}
</style>
