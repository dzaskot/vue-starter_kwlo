<template>
  <div>
    <h1>Witaj w systemie zapisów na zajęcia</h1>
    <div v-if= "authenticatedUserName !==''">
      <h3>Witaj {{authenticatedUserName}}</h3>
      <a @click="logOut()">Wyloguj </a>
    </div>
    <div v-else>
      <login-form @login="logIn($event)"></login-form>
      <!--<label>Zaloguj się emailem </label>
      <input type="email" v-model = "email">
      <button class="myButton" @click="logIn()"> Zaloguj</button>-->
    </div>
  </div>
</template>

<script>
import LoginForm from "./LoginForm";
import "milligram";

export default {
  components: {LoginForm},
  data() {
    return {
      authenticatedUserName:''
    };
  },
  methods: {
    logIn(username) {
      this.authenticatedUserName = username;
    },
    logOut() {
      this.authenticatedUserName = '';
    }
  }
}
</script>
<style>
</style>
