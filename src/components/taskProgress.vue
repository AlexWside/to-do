<template>
  <div class="task-progress">
    <span class="progress-value">{{progress}}%</span>
    <div class="progress-bar" :style="{width: progress + '%'}"></div>
  </div>
</template>

<script>
export default {
  props: {
    progress: {
      type: Number,
      default: 0
    }
  }

}
</script>

<style>

.task-progress{
  position: relative;
  width:50%;
  border: 1px solid #ccc;
  border-radius: 8px;
  margin-bottom: 15px;
  display:flex;
  flex-direction: column;
  align-items: center;
}


.progress-bar{
  position: absolute;
  background-color: #70db70;
  border-radius: 8px;
  height: 100%;
 align-self: flex-start;
  }

.progress-value{
  z-index:1;
}
</style>