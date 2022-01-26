<template>
  <header>
    <h1>{{ title }}</h1>
    <TaskButton text="Add Task" color="green" />
    <TaskButton text="Update Task" color="black" />
    <TaskButton text="Delete Task" color="red" />
  </header>
</template>

<script>
import TaskButton from "./TaskButton.vue";
export default {
  name: "Header",
  props: {
    title: {
      type: String,
      required: true,
      default: "Task Tracker",
    },
  },
  components: {
    TaskButton,
  },
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}
</style>
