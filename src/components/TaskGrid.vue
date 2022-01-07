<template>
   <div class="tasks-grid">
     <template v-if="tasks.length">
      <Task v-for="(task,i) in tasks" :key="task.name"
      @taskDeleted="$emit('taskDeleted', i)"
      @chagedState="$emit('chagedState', i)"
      :task="task">
         
      </Task>
     </template>
     <p v-else class="no-task">Sem tarefas</p>
   </div>
</template>

<script>
import Task from './task.vue'
export default {
  components: { Task },
    props: {
      tasks: {
        type:Array, riquired: true
      }
    }
}
</script>

<style>

.tasks-grid{

display: flex;
justify-content: center;
flex-wrap: wrap;
}

.tasks-grid .task{
  margin: 10px;
}

.no-task{
    color: #AAA;
    font-size: 1.7rem;
}
</style>