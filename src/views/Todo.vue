<template>
  <div class="todo">
    <h1>To Do</h1>
     <form @submit.prevent="handleSubmit">
      <input v-model.lazy="newTodo" placeholder="Type List" />
      <button type="submit">Submit</button>
    </form>
    <TodoList :todos="todos" />
  </div>
</template>

<script>
import TodoList from "../components/TodoList.vue";

export default {
  components: {
    TodoList,
  },
  data() {
    return {
      newTodo: "",
      todos: [],
      nextTodoId: 0,
    };
  },
  methods: {
    handleSubmit() {
      if (!this.newTodo) return;
      this.todos.push({
        id: this.nextTodoId++,
        title: this.newTodo,
      });
      this.newTodo = "";
    },
  },
};

</script>

<style>
.todo {
  width: 100%;
  padding: 50px 0 0 10px;
}
</style>