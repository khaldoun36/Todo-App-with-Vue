<template>
  <form class="add__todo" @submit.prevent="sendEvent">
    <input
      type="text"
      placeholder="Add todo"
      v-model="newTodo"
      @keydown.enter.prevent="sendEvent"
    />
    <button>Add todo</button>
  </form>
</template>

<script>
import { ref } from "@vue/reactivity";
export default {
  setup(props, context) {
    const newTodo = ref(null);
    // send custome event to the parent component
    const sendEvent = () => {
      context.emit("handleKeydown", newTodo.value);
      newTodo.value = null;
    };
    return { newTodo, sendEvent };
  },
};
</script>

<style scoped>
.add__todo {
  margin-bottom: 2.5rem;
  font-size: 1.75rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.add__todo input {
  width: 80%;
  padding: 0.75em;
  font-size: 1.25rem;
  border: 1px solid rgba(0, 0, 0, 0.1);
}

button {
  align-items: center;
  background-color: #ffffff;
  border: 1px solid rgba(0, 0, 0, 0.1);
  border-radius: 0.25rem;
  box-shadow: rgba(0, 0, 0, 0.02) 0 1px 3px 0;
  color: rgba(0, 0, 0, 0.85);
  cursor: pointer;
  display: inline-flex;
  font-size: 1.25rem;
  font-weight: 600;
  justify-content: center;
  line-height: 1.25;
  margin: 0;
  min-height: 3rem;
  padding: calc(0.875rem - 1px) calc(1.5rem - 1px);
  position: relative;
  text-decoration: none;
  transition: all 250ms;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
  vertical-align: baseline;
  width: auto;
}
</style>
