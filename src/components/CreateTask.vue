<template>
  <div class="createTask">
    <form @submit.prevent="handleSubmit">
      <input type="text" placeholder="Enter a new task" v-model="newTask" />
      <button>Submit</button>
    </form>
  </div>
</template>

<script>
import { inject, ref } from "vue";
export default {
  name: "CreateTask",

  setup() {
    let newTask = ref("");
    const inputRef = ref();
    let newTodo = inject("c_todoList");

    function handleSubmit() {
      newTodo.push(newTask.value);
      newTask.value = "";
    }

    return {
      newTask,
      newTodo,
      handleSubmit,
      inputRef,
    };
  },
};
</script>

<style scoped></style>
