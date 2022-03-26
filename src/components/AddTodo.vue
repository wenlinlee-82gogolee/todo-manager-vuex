<template>
  <div>
    <h2>Add Todo</h2>
    <div class="add">
      <form @submit.prevent="handleSubmit">
        <input type="text" v-model="title" placeholder="Add Todo..." />
        <input type="submit" value="Submit" />
      </form>
    </div>
  </div>
</template>

<script>
import { mapActions } from 'vuex';
export default {
  name: 'AddTodo',
  data() {
    return {
      title: '',
    };
  },
  methods: {
    ...mapActions(['addTodo']),
    handleSubmit() {
      this.addTodo(this.title);
    },
  },
};
</script>

<style scoped>
form {
  display: flex;
}
input[type='text'] {
  flex: 10;
  padding: 1rem;
  border: 1px solid var(--color-primary);
  outline: 0;
}
input[type='submit'] {
  flex: 2;
  background: var(--color-primary);
  color: #fff;
  border: 1px var(--color-primary) solid;
  cursor: pointer;
}
</style>
