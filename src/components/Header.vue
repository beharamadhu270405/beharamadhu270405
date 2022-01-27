<template>
  <header>
    <h1>{{ title }}</h1>
    <TaskButton text="Add Task" color="green" />
  </header>
</template>

<script>
import TaskButton from "./TaskButton.vue";
export default {
  name: "Header",
  props: {
    title: {
      type: String,
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
