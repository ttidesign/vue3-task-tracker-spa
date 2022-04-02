<template>
  <div>
    <AddTask @add-task="addTask" v-if="showAddTask" />
  </div>
  <TasksComp
    :tasks="tasks"
    @delete-task="deleteTask"
    @toggle-reminder="toggleReminder"
  />
</template>

<script>
// @ is an alias to /src
import TasksComp from "../components/TasksComp.vue";
import AddTask from "../components/AddTask.vue";
export default {
  name: "HomeView",
  props: {
    showAddTask: Boolean,
  },
  components: {
    TasksComp,
    AddTask,
  },
  data() {
    return {
      tasks: [],
    };
  },
  methods: {
    async addTask(task) {
      const res = await fetch("api/tasks/", {
        method: "POST",
        headers: {
          "Content-type": "application/json",
        },
        body: JSON.stringify(task),
      });
      const data = await res.json();
      this.tasks = [...this.tasks, data];
    },
    async deleteTask(id) {
      if (confirm("Are you sure?")) {
        const res = await fetch(`api/tasks/${id}`, {
          method: "DELETE",
        });
        res.status === 200
          ? (this.tasks = this.tasks.filter((task) => task.id !== id))
          : alert("Error deleting task");
      }
    },
    async toggleReminder(id) {
      const taskToToggle = await this.fetchSingleAPI(id);
      const updTask = { ...taskToToggle, reminder: !taskToToggle.reminder };
      const res = await fetch(`api/tasks/${id}`, {
        method: "PUT",
        headers: {
          "Content-type": "application/json",
        },
        body: JSON.stringify(updTask),
      });
      const data = await res.json();
      this.tasks = this.tasks.map((task) =>
        task.id === id ? { ...task, reminder: data.reminder } : task
      );
    },
    async fetchAPI() {
      const res = await fetch("api/tasks");
      const results = await res.json();
      return results;
    },
    async fetchSingleAPI(id) {
      const res = await fetch(`api/tasks/${id}`);
      const result = await res.json();
      return result;
    },
  },
  async created() {
    this.tasks = await this.fetchAPI();
  },
};
</script>
