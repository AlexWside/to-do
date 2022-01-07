<template>
  <div id="app">
    <h1>Tarefas</h1>
    <NewTask @taskAdded="addTask" />
    <TaskGrid @taskDeleted="deleteTask" @chagedState="statusChanger" :tasks="tasks" />



  </div>
</template>

<script>
import NewTask from "./components/newTask.vue";
import TaskGrid from "./components/TaskGrid.vue";
export default {
  components: { TaskGrid, NewTask },
  data() {
    return {
      tasks: [
        { name: "lavar roupa", status: false },
        { name: "comprar comida", status: true },
      ],
      id: ""

    };
  },
	methods: {
		addTask(task){


				const SameName = (valor) => { return valor.name === task.name }

				const Result = this.tasks.filter(SameName).length == 0

				if (Result){
				this.tasks.push({
					name: task.name,
					status: task.status || true
				});

				}
				

		},
    deleteTask(i){
          this.tasks.splice(i,1)
    },
    statusChanger(i){
        this.tasks[i].status = !this.tasks[i].status 
    }
	}
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