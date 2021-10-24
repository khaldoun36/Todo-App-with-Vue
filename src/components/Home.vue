<template>
  <div class="home">
    <h1>Todo List</h1>
    <InputForm @handleKeydown="addNewTodo" />
    <TodoList :todosProp="todos" @deleteTodo="deleteTodo" />
  </div>
</template>

<script>
import { computed, ref } from "@vue/reactivity";
// import componenets
import TodoList from "./TodoList.vue";
import InputForm from "./InputForm.vue";
export default {
  components: { TodoList, InputForm },
  setup() {
    const todos = ref([
      {
        id: 1,
        title: "Do the dishes",
        isCompleted: false,
      },
    ]);

    // generate a unique number
    const { v4: uuidv4 } = require("uuid");

    const addNewTodo = (newTodo) => {
      todos.value.push({
        id: uuidv4(),
        title: newTodo,
        isCompleted: false,
      });
    };

    // delete todo

    const deleteTodo = (id) => {
      const newTodos = todos.value.filter((todo) => todo.id !== id);
      todos.value = newTodos;
    };

    return { todos, addNewTodo, deleteTodo };
  },
};
</script>

<style>
h1 {
  margin-bottom: 2.5rem;
  text-align: center;
}
.home {
  max-width: 900px;
  width: 100%;
  margin: 6rem auto;
}
</style>
