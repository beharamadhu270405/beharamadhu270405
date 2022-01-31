<template>
  <header>
    <h1>{{ title }}</h1>
    <AddTaskButton
      @toggle-add-task-button="$emit('toggle-add-task-button')"
      text="Add Task"
      color="green"
    />
  </header>
</template>

<script>
import AddTaskButton from "./AddTaskButton.vue";
export default {
  name: "Header",
  props: {
    title: {
      type: String,
      default: "Task Tracker",
    },
  },
  components: {
    AddTaskButton,
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
