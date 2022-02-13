<template>
  <div class="btn-group">
    <button class="btn reset" @click="$emit('resetHandler')">Start!</button>
    <button class="btn set">Set Timer</button>
  </div>
</template>

<script>
export default {
  emits: ["resetHandler"],
};
</script>

<style scoped>
.btn {
  border: 1px solid #444;
  font-family: Montserrat;
  padding: 5px 10px;
  font-size: 1rem;
  cursor: pointer;
  background-color: #fff;
  color: #444;
  margin-top: 30px;
}
.btn.set {
  margin-left: 10px;
}
</style>
