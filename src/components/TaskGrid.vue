<template>
   <div class="tasks-grid">
     <template v-if="tasks.length">
      <Task v-for="task in tasks" :key="task.name"
      
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

</style>