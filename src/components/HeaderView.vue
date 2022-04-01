<template>
  <header>
    <h1>{{ title }}</h1>
    <ButtonComp text="Add Task" color="lightskyblue" />
  </header>
</template>

<script>
import ButtonComp from "./ButtonComp.vue";
export default {
  name: "HeaderView",
  props: {
    title: String,
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
