<template>
  <div>
    <h2>Todos</h2>
    <div class="legend">
      <span>Double click to mark as complete</span>
      <span> <span class="incomplete-box"></span>=Incomplete </span>
      <span> <span class="complete-box"></span>=Complete </span>
    </div>
    <div class="todos">
      <div
        @dblclick="handleClick(todo)"
        v-for="todo in allTodos"
        :key="todo.id"
        class="todo"
        :class="{ 'is-complete': todo.completed }"
      >
        {{ todo.title }}
        <span class="material-icons" @click="deleteTodo(todo.id)"> close</span>
      </div>
    </div>
  </div>
</template>

<script>
import { mapGetters, mapActions } from 'vuex';
export default {
  name: 'Todos',
  methods: {
    ...mapActions(['fetchTodos', 'deleteTodo', 'updateTodo']),
    handleClick(todo) {
      const updTodo = {
        id: todo.id,
        title: todo.title,
        completed: !todo.completed,
      };

      this.updateTodo(updTodo);
    },
  },
  computed: mapGetters(['allTodos']),
  created() {
    this.fetchTodos();
  },
};
</script>

<style scoped>
.todos {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 1rem;
}
.todo {
  border: 1px solid #ccc;
  background: var(--color-primary);
  padding: 1rem;
  border-radius: 5px;
  text-align: center;
  position: relative;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.legend {
  display: flex;
  justify-content: space-around;
  margin-bottom: 1rem;
}
.complete-box {
  display: inline-block;
  width: 1rem;
  height: 1rem;
  background: #557b83;
}
.incomplete-box {
  display: inline-block;
  width: 1rem;
  height: 1rem;
  background: var(--color-primary);
}
.is-complete {
  background: #557b83;
  color: #fff;
}
@media (max-width: 31.25em) {
  .todos {
    grid-template-columns: 1fr;
  }
}
</style>
