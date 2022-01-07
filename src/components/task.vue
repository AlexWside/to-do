<template>
  <div class="task" @click="$emit('chagedState', task )" :class="stateClass">
    <span @click="$emit('taskDeleted', task)" class="clone">x</span>
    <p>{{ task.name }}</p>
  </div>
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
    stateClass() {
      return {
        pending: this.task.status,
        done: !this.task.status,
      };
    },
  },
};
</script>

<style>
.task {
  position: relative;
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

.pending {
  background-color: #ff6666;
  border-right: #ff3c3c solid 5px;
}

.pending {
  background-color: #ff6666;
  border-right: #ff3c3c solid 12px;
}

.done {
  color: #ddd;
  background-color: #70db70;
  border-right: #33cc33 solid 12px;
  text-decoration: line-through;
}

.done .clone{
  background-color: #51b051;
}

.pending .clone{
  background-color: #cc3c3c;
}

.clone {
     position: absolute;
     right: 10px;
     top: 10px;
     font-size: 0.9rem;
     font-weight: 600;
     height: 20px;
     width: 20px;
     border-radius: 10px;
     display: flex;
     justify-content: center;
}
</style>