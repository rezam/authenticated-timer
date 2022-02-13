<template>
  <div class="modal">
    <div class="modal-body">
      <p>Login</p>
      <form @click.prevent>
        <div class="group-control">
          <label for="uername">Username</label>
          <input type="text" name="username" ref="usernameInput" />
        </div>
        <div class="group-control">
          <label for="password">Password</label>
          <input type="text" name="password" ref="passwordInput" />
        </div>
        <p class="error" v-show="showError || isError">
          Please enter a valid username and password
        </p>
        <button @click="submitData" type="submit" class="submit">Login</button>
        <button @click="$emit('modalClose')" class="close">Close</button>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  emits: ["modalClose", "submitLogin"],
  props: ["isError"],
  data() {
    return {
      showError: false,
      enteredUsername: "",
      enteredPassword: "",
    };
  },
  methods: {
    submitData() {
      this.enteredUsername = this.$refs.usernameInput.value;
      this.enteredPassword = this.$refs.passwordInput.value;
      if (this.enteredUsername.length > 0 && this.enteredPassword.length > 0) {
        this.emitSubmitLogin();
      } else {
        this.showError = true;
      }
    },
    emitSubmitLogin() {
      this.$emit("submitLogin", this.enteredUsername, this.enteredPassword);
    },
  },
};
</script>

<style scoped>
.error {
  color: crimson;
  font-size: 12px;
}
.modal {
  background-color: rgba(0, 0, 0, 0.9);
  width: 100%;
  height: 100vh;
  position: absolute;
  top: 0;
  text-align: center;
}
.modal-body .group-control {
  margin-bottom: 10px;
}
.modal-body .group-control label {
  padding-bottom: 4px;
}
.modal-body .group-control input {
  font-size: 18px;
  border: 1px solid #aaa;
  outline: none;
}
.modal-body .group-control label,
.modal-body .group-control input {
  display: flex;
  width: 260px;
}
.modal-body button {
  font-family: Montserrat;
  margin-top: 20px;
  border: 1px solid #aaa;
  background-color: #fff;
  padding: 5px 10px;
  cursor: pointer;
}
.modal-body button.submit {
  margin-right: 10px;
}
.modal-body {
  position: absolute;
  margin: 0 auto;
  width: 40vh;
  top: 0;
  transform: translateY(50%);
  left: 0;
  right: 0;
  background-color: #ddd;
  padding: 10px 20px;
}
</style>