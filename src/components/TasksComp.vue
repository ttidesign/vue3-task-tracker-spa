<template>
  <div v-for="task in tasks" :key="task.id">
    <Task :task="task" />
  </div>
</template>
<script>
import Task from "./TaskComp.vue";
export default {
  name: "TasksComp",
  props: {
    tasks: Array,
  },
  components: {
    Task,
  },
};
</script>
