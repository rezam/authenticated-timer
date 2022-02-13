<template>
  <div class="header">
    <p>Sale Starts at:</p>
    <button v-if="!isLogin" @click="$emit('modalHandler')" class="log in">Login</button>
    <button v-else @click="$emit('logoutHandler')" class="log out">Logout</button>
  </div>
</template>

<script>
export default {
  emits: ["modalHandler", "logoutHandler"],
  props: ["isLogin"],
};
</script>

<style scoped>
.header {
  font-size: 1.2rem;
  position: relative;
  width: 100%;
}
.header p:first-child {
  text-align: center;
}
.header .log {
  position: absolute;
  top: 20px;
  right: 50px;
  font-size: 15px;
  padding: 3px 7px;
  cursor: pointer;
  color: #444;
  text-decoration: underline;
  transition: all 0.3s;
  background: #fff;
  border: none;
  font-family: Montserrat;
}
.header .btn.log:hover {
  color: #111;
}
@media screen and (max-width: 500px) {
  .header .log {
    top: 0px;
  }
}
</style>
