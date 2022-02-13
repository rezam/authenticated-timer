<template>
  <Header @modalHandler="modalStat" @logoutHandler="loginStat" :isLogin="isLogin"/>
  <Counter :sec="seconds" :min="minutes" />
  <Buttons v-if="isLogin" @resetHandler="runDate" />
  <LoginModal :isError="isError" @submitLogin="checkLogin" @modalClose="modalStat" v-if="showModal" />
</template>

<script>
import Counter from "./components/Counter.vue";
import Header from "./components/Header.vue";
import Buttons from "./components/Buttons.vue";
import LoginModal from "./components/LoginModal.vue";

export default {
  name: "App",
  components: {
    Counter,
    Header,
    Buttons,
    LoginModal,
  },
  data() {
    return {
      seconds: 59,
      minutes: 59,
      isLogin: false,
      isError: false,
      showModal: false,
      username: "admin",
      password: "reza",
    };
  },
  methods: {
    modalStat() {
      this.showModal = !this.showModal;
    },
    loginStat() {
      this.isLogin = !this.isLogin;
    },
    checkLogin(username, password) {
      if(username === this.username && password === this.password) {
        this.modalStat();
        this.isLogin = true;
        this.isError = false;
      } else {
        this.isError = true;
        this.isLogin = false;
      }
    },
    runDate() {
      const counterTime = setInterval(() => {
        if (this.seconds > 0) {
          this.seconds--;
        } else {
          this.seconds = 59;
          this.minutes ? this.minutes-- : (this.minutes = 59);
        }
        this.minutes === 0 && this.seconds === 0
          ? clearInterval(counterTime)
          : "";
      }, 1000);
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Montserrat:wght@300&display=swap");

#app {
  font-family: Montserrat;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>
