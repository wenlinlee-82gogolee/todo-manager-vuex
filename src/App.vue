<template>
  <div>
    <div class="container">
      <h1 class="heading">WLL's Todo Manager</h1>
      <AddTodo />
      <FilterTodos />
      <Todos />
    </div>
  </div>
</template>

<script>
import Todos from './components/Todos.vue';
import AddTodo from './components/AddTodo.vue';
import FilterTodos from './components/FilterTodos.vue';

export default {
  name: 'App',
  components: {
    Todos,
    AddTodo,
    FilterTodos,
  },
};
</script>

<style>
:root {
  --color-primary: #39aea9;
}
html {
  font-size: 62.5%;
  box-sizing: border-box;
}
body {
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  line-height: 1.6;
  background: #ebf3cb;
  font-size: 1.6rem;
}
.heading {
  font-size: 3.5rem;
  text-align: center;
  color: #557b83;
}
.container {
  max-width: 110rem;
  margin: auto;
  overflow: auto;
  padding: 0 2rem;
}
</style>
