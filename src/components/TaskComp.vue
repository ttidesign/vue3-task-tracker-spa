<template>
  <div
    :class="[task.reminder ? 'reminder' : '', 'task']"
    @dblclick="$emit('toggle-reminder', task.id)"
  >
    <h3>
      {{ task.text }}
      <i class="fas fa-times" @click="removeTask(task.id)"></i>
    </h3>
    <p>{{ task.date }}</p>
  </div>
</template>
<script>
export default {
  name: "TaskComp",
  props: {
    task: Object,
  },
  methods: {
    removeTask(id) {
      this.$emit("delete-task", id);
    },
  },
};
</script>
<style scope>
.fas {
  color: red;
}
.task {
  background: #f4f4f4;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
}
.task.reminder {
  border-left: 5px solid green;
}
.task h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>
