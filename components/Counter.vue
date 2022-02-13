<template>
  <div class="content">{{ min }} : {{ sec }}</div>
</template>

<script>
export default {
  props: {
    days: Number,
    hours: Number,
    min: Number,
    sec: Number,
  },
};
</script>

<style scoped>
.content {
  font-size: 2.3rem;
  letter-spacing: 3px;
  color: #333;
}
</style>
