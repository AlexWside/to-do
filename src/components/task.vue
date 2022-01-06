<template>
  <div class="task" 
  :class="stateClass"
  >{{task.name}}</div>
</template>

<script>
export default {
  props: {
    task: {
      type: Object,
      required: true,
    },
  },
  computed: {
     stateClass(){
       return {
              pending: this.task.status,
              done: !this.task.status
       }
     }
  }
};
</script>

<style>

.task{
  box-sizing: border-box;
  width: 350px;
  height: 150px;
  padding: 10px;
  border-radius: 8px;
  font-size: 2rem;
  font-weight: 300;
  cursor: pointer;
  user-select: none;
  display: flex;
  justify-content: center;
  align-items: center;
}


.pending{
  background-color: #ff6666;
  border-right: #ff3c3c solid 5px;
}

.pending{
  background-color: #ff6666;
  border-right: #ff3c3c solid 12px;
}

.done{
  color: #ddd;
  background-color: #70db70;
  border-right: #33cc33 solid 12px;
  text-decoration: line-through;
}
</style>