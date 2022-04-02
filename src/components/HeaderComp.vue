<template>
  <header>
    <h1>{{ title }}</h1>
    <ButtonComp
      v-show="homePage"
      :text="showAddTask ? 'Close' : 'Add Task'"
      :color="showAddTask ? 'red' : 'lightskyblue'"
      @btn-click="$emit('toggle-add-task')"
    />
  </header>
</template>

<script>
import ButtonComp from "./ButtonComp.vue";
export default {
  name: "HeaderView",
  props: {
    title: String,
    showAddTask: Boolean,
  },
  computed: {
    homePage() {
      if (this.$route.path === "/") {
        return true;
      }
      return false;
    },
  },
  components: {
    ButtonComp,
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
