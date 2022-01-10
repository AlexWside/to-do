<template>
  <div id="app">
    <TaskProgress :progress="progress" />
    <h1>Tarefas</h1>
    <NewTask @taskAdded="addTask" />
    <TaskGrid
      @taskDeleted="deleteTask"
      @chagedState="statusChanger"
      :tasks="tasks"
    />
  </div>
</template>

<script>
import NewTask from "./components/newTask.vue";
import TaskGrid from "./components/TaskGrid.vue";
import TaskProgress from "./components/taskProgress.vue";
export default {
  components: { TaskGrid, NewTask, TaskProgress },
  data() {
    return {
      tasks: [],
      id: "",
    };
  },
  methods: {
    addTask(task) {
      const SameName = (valor) => {
        return valor.name === task.name;
      };

      const Result = this.tasks.filter(SameName).length == 0;

      if (Result) {
        this.tasks.push({
          name: task.name,
          status: task.status || true,
        });
      }
    },
    deleteTask(i) {
      this.tasks.splice(i, 1);
    },
    statusChanger(i) {
      this.tasks[i].status = !this.tasks[i].status;
    },
  },
  computed: {
    progress() {
      const total = this.tasks.length;
      const concluido = this.tasks.filter((t) => !t.status).length;
      return Math.round((concluido / total) * 100) || 0;
    },
  },
  watch: {
    tasks: {
      deep: true,
      handler(){
        localStorage.setItem("tasks", JSON.stringify(this.tasks));
      }
    },
  },
  created() {
    const json = localStorage.getItem("tasks");
    const array = JSON.parse(json);
    if (Array.isArray(array)) {
      this.tasks = array
    }else {
        this.tasks = []
    }
  },
};
</script>

<style>
body {
  font-family: "Lato", sans-serif;
  background: linear-gradient(to right, rgb(22, 34, 42), rgb(58, 96, 115));
  color: #fff;
}

#app {
  display: flex;
  flex: 1;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

#app h1 {
  margin-bottom: 5px;
  font-weight: 300;
  font-size: 3rem;
}
</style>