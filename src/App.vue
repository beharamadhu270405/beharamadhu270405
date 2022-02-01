<template>
  <div class="container">
    <Header
      @toggle-add-task-button="toggleAddTask"
      :showAddTasksForm="showAddTasksForm"
    />
    <div v-show="showAddTasksForm">
      <AddTaskForm @add-task="addTask" />
    </div>

    <Tasks
      @toggle-remiander="toggleRemainder"
      @delete-task="deleteTask"
      :tasks="tasks"
    />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Tasks from "./components/Tasks.vue";
import AddTaskForm from "./components/AddTaskForm.vue";
export default {
  name: "App",
  components: {
    Header,
    Tasks,
    AddTaskForm,
  },
  data() {
    return { tasks: [], showAddTasksForm: false };
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: "Doctors Appointment",
        day: "Jan 27th at 8:30pm",
        reminder: true,
      },
      {
        id: 2,
        text: "Code Review",
        day: "Jan 28th at 4:30pm",
        reminder: true,
      },
      {
        id: 3,
        text: "Cricket Match",
        day: "Jan 30th at 12:30pm",
        reminder: false,
      },
    ];
  },
  methods: {
    toggleAddTask() {
      this.showAddTasksForm = !this.showAddTasksForm;
    },
    addTask(task) {
      this.tasks = [...this.tasks, task];
    },
    deleteTask(taskId) {
      if (confirm("Are you sure you want to delete?")) {
        console.log(`Deleting the Task:${taskId}`);
        this.tasks = this.tasks.filter((task) => task.id != taskId);
      }
    },
    toggleRemainder(taskId) {
      console.log(`Toggling Remainder of the Task:${taskId}`);
      this.tasks = this.tasks.map((task) =>
        task.id === taskId ? { ...task, reminder: !task.reminder } : task
      );
      console.table(this.tasks);
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap");
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: "Poppins", sans-serif;
}
.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}

.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>