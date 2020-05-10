<template>
  <div id="app">

    <h1>System do zapisów na zajęcia</h1>

    <div v-if="authenticatedUsername != ''">
      <user-panel :username="authenticatedUsername" @logout="logMeOut"></user-panel>
      <meeting-page></meeting-page>

    </div>
    <div v-else>
      <login-form @login="logMeIn($event)"></login-form>

    </div>

  </div>
</template>

<script>
  import "milligram";
  import LoginForm from "./LoginForm";
  import UserPanel from "./UserPanel";
  import MeetingPage from "./meetings/MeetingPage";

export default {
  components: {LoginForm, UserPanel, MeetingPage},
  data() {
    return {
      authenticatedUsername: ''
    };
  },
  methods: {
    alertMyEmail() {
      alert(this.email);
    },
    logMeIn(username) {
      this.authenticatedUsername = username;
    },
    logMeOut() {
      this.authenticatedUsername = '';
      this.email = '';  // to może być również w this.logMeIn(), nie ma znaczenia
    }

  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /*text-align: center;*/
  color: #2c3e50;
  margin-top: 60px;
}
#email-box {
  width: 50%;
}
</style>
