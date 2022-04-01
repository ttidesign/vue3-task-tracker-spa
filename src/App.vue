<template>
  <div class="container">
    <HeaderView title="Task Tracker" />
    <TasksComp :tasks="tasks" />
  </div>
  <router-view />
</template>
<script>
import HeaderView from "./components/HeaderView.vue";
import TasksComp from "./components/TasksComp.vue";

export default {
  name: "App",
  components: {
    HeaderView,
    TasksComp,
  },
  data() {
    return {
      tasks: [],
    };
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: "Doctor Appointment",
        date: "March 31 2022",
        reminder: true,
      },
      {
        id: 2,
        text: "Cancel Appointment with doctor",
        date: "March 31 2022",
        reminder: false,
      },
      {
        id: 3,
        text: "Call Doctor to Schedule",
        date: "March 31 2022",
        reminder: true,
      },
    ];
  },
};
</script>

<style lang="scss">
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

nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
