<template>
  <CreateTask />

  <li v-for="(task, index) in todoList" :key="index">
    {{ task }}
    <button @click="editTask(index)">Edit</button>
    <button @click="deleteTask(index)">Delete</button>
  </li>
</template>

<script>
import CreateTask from "./components/CreateTask.vue";
import { provide, reactive, toRefs } from "vue";
export default {
  name: "App",
  components: { CreateTask },
  setup() {
    let state = reactive({
      todoList: [],
    });
    function editTask(index) {
      console.log(index)
      let edit = prompt("Enter a new task");
      this.todoList.splice(index, 1, edit);
    }
    function deleteTask(index) {
      this.todoList.splice(index, 1);
    }
    provide("c_todoList", state.todoList);
    return {
      ...toRefs(state),
      editTask,
      deleteTask,
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>
