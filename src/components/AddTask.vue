<template>
  <form @submit="onSubmit" class="add-for">
    <div class="form-control">
      <label for="addTask">Task</label>
      <input
        type="text"
        v-model="text"
        name="text"
        placeholder="Add Task"
        id="addTask"
      />
    </div>
    <div class="form-control">
      <label for="dayTime">Day & Time</label>
      <input
        type="text"
        v-model="day"
        id="dayTime"
        name="day"
        placeholder="Add Day & Time"
      />
    </div>
    <div class="form-control form-control-check">
      <label for="reminderCheck">Set Reminder</label>
      <input
        type="checkbox"
        v-model="reminder"
        id="reminerCheck"
        name="reminder"
      />
    </div>
    <input type="submit" value="Save Task" class="btn btn-block" />
  </form>
</template>

<script>
export default {
  name: "AddTask",
  data() {
    return {
      text: "",
      day: "",
      reminder: false,
    };
  },
  methods: {
    onSubmit(e) {
      e.preventDefault();

      if (!this.text) {
        alert("Please add a Task");
        return;
      }

      const NewTask = {
        text: this.text,
        day: this.day,
        reminder: this.reminder,
      };

      this.$emit("add-task", NewTask);

      this.text = "";
      this.day = "";
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
  widows: 100%;
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
