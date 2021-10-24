<template>
  <div class="todo__list">
    <div v-for="todo in todosProp" :key="todo.id">
      <SingleTodo :todoProp="todo" @handleDelete="handleDelete" />
    </div>
  </div>
</template>

<script>
// Import Componenets
import SingleTodo from "./SingleTodo.vue";
export default {
  props: ["todosProp"],
  components: { SingleTodo },
  setup(props, context) {
    const handleDelete = (id) => {
      context.emit("deleteTodo", id);
    };
    return { handleDelete };
  },
};
</script>

<style>
.todo__list {
  text-align: center;
}
</style>
