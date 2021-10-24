<template>
  <div class="single__todo" :class="{ completed: isComp }">
    <h2 class="todo__title">{{ todoProp.title }}</h2>
    <div class="buttons">
      <p class="delete" @click="sendDelete">Delete</p>
      <p class="mark__complete" @click="handleComplete">
        Complete
      </p>
    </div>
  </div>
</template>

<script>
import { ref } from "@vue/reactivity";
export default {
  props: ["todoProp"],
  setup(props, context) {
    // evaluate is completed truthness
    const isComp = ref(false);
    // handle the completed todos
    const handleComplete = () => {
      isComp.value = !isComp.value;
    };

    // send the delete event to the home component
    const sendDelete = () => {
      context.emit("handleDelete", props.todoProp.id);
    };

    return { handleComplete, isComp, sendDelete };
  },
};
</script>

<style>
.single__todo {
  display: flex;
  justify-content: space-between;
  align-items: center;
  text-align: left;
  font-size: 1.25rem;
  margin-bottom: 1em;
  padding: 1em;
  box-shadow: rgba(149, 157, 165, 0.2) 0px 8px 24px;
}

.completed {
  text-decoration: line-through;
}
.buttons {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.mark__complete {
  padding-left: 2em;
  color: #5b8e7d;
}

.delete {
  color: #bc4b51;
}
</style>
