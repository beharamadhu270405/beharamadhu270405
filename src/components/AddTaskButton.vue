<template>
  <button
    class="btn"
    :style="{ background: color }"
    @click="$emit('toggle-add-task-button')"
  >
    {{ text }}
  </button>
</template>

<script>
export default {
  name: "AddTaskButton",
  props: {
    text: {
      type: String,
    },
    color: {
      type: String,
    },
  },
  methods: {},
};
</script>

<style scoped>
</style>
