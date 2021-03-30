<template>
<h1>Vue todo-app</h1>
<form action="" @submit.prevent="addNewTodo">
  <label for="">New Todo</label>
  <input v-model="newTodo" type="text" name="newTodo">
  <button>Add New Todo</button>
</form>
<div class="">
  <button @click="markAllDone()">Mark All Done</button>
  <ul>
    <li v-for="(todo, index) in todos" :key="todo.id" class="todo">
      <h3 :class="{done: todo.done}" @click="toggleDone(todo)">{{todo.content}}</h3>
      <button @click="removeTodo(index)">Remove todo</button>
    </li>
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
    });
    newTodo.value = ''; //vacía el input luego del submit
  }

  function toggleDone(todo){
    todo.done = !todo.done;
  }

  function removeTodo(index){
    todos.value.splice(index,1);
  }
  function markAllDone(){
    todos.value.forEach(todo=> todo.done = true);
}
  return{
    todos,
    newTodo,
    addNewTodo,
    toggleDone,
    removeTodo,
    markAllDone
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
.todo{
  cursor: pointer;
}
.done {
text-decoration: line-through;
}
</style>
