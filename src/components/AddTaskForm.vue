<template>
  <form class="add-form" @submit="addTask">
    <div class="form-control">
      <label for="taskname">Task Name:</label>
      <input
        type="text"
        class="form-control-input"
        v-model="taskname"
        placeholder="Enter Task Name"
        id="taskname"
      />
    </div>
    <div class="form-control">
      <label for="datetime">Day && Time:</label>
      <input
        type="datetime-local"
        class="form-control-input"
        v-model="time_and_date"
        placeholder="Enter Day and Time"
        id="datetime"
      />
    </div>
    <div class="form-control-check">
      <label class="form-check-label">
        <input class="form-check-input" v-model="reminder" type="checkbox" />
        Remember Task
      </label>
    </div>
    <input type="submit" value="Save Task" class="btn btn-block" />
  </form>
</template>

<script>
export default {
  name: "AddTaskForm",
  methods: {
    addTask(e) {
      e.preventDefault();
      if (!this.taskname) {
        alert("Please Add the Task Name");
        return;
      }
      const newTask = {
        id: Math.floor(Math.random() * 10000),
        text: this.taskname,
        day: this.time_and_date,
        reminder: this.reminder,
      };
      this.$emit("add-task", newTask);
      console.table(newTask);
      this.taskname = "";
      this.time_and_date = "";
      this.reminder = false;
    },
  },
};
</script>


<style scoped>
.add-form {
  margin-bottom: 40px;
}
.form-control {
  margin: 20px 0;
}
.form-control label {
  display: block;
}
.form-control input {
  width: 100%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
}
.form-control-check {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.form-control-check label {
  flex: 1;
}
.form-control-check input {
  flex: 2;
  height: 20px;
}
</style>