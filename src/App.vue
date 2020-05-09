<template>
  <div>
    <h1>Witaj w systemie zapisów na zajęcia</h1>
    <div v-if= "authenticatedUserName !==''">
      <logout :username="authenticatedUserName" @logout="logOut()"></logout>
      <meeting-page></meeting-page>
    </div>
    <div v-else>
      <login-form @login="logIn($event)" button-label="Zaloguj się"></login-form>
    </div>
  </div>
</template>

<script>
import LoginForm from "./LoginForm";
import Logout from "./Logout";
import MeetingPage from "./meetings/MeetingPage";
import "milligram";

export default {
  components: {LoginForm,Logout,MeetingPage},
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
