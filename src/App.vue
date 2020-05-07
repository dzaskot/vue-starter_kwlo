<template>
  <div>
    <h1>Witaj w systemie zapisów na zajęcia</h1>
    <div v-if= "authenticatedUserName != ''">
      <h3>Witaj {{authenticatedUserName}}</h3>
      <a @click="logOut()">Wyloguj </a>
    </div>
    <div v-else>
      <label>Zaloguj się emailem </label>
      <input type="email" v-model = "email">
      <button class="myButton" @click="logIn()"> Zaloguj</button>
    </div>
  </div>
</template>

<script>
import "milligram";

export default {
  data() {
    return {
      email: '',
      authenticatedUserName:''
    };
  },
  methods: {
    logIn(email) {
      this.authenticatedUserName = this.email;
    },
    logOut(email) {
      this.email = '';
      this.authenticatedUserName = '';
    }
  }
}
</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.myButton {
  margin-left: 5px
}
</style>
