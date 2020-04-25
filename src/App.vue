<template>
  <div id="app">

    <h1>Witaj w systemie zapisów na zajęcia</h1>

    <div v-if="authenticatedUsername != ''">
      <h3>Witaj {{authenticatedUsername}}</h3>
      <a @click="logMeOut">Wyloguj</a>
    </div>
    <div v-else>
      <input type="text" v-model="email">
      <button @click="logMeIn()">Zaloguj</button>
    </div>

<!--
    <div v-if="email.length < 10">Ale masz krótki adres!</div>
    <div v-else-if="email.length < 15">Twój adres e-mail jest w sam raz.</div>
    <div v-else>Twój adres e-mail jest stanowczo za długi.</div>

    <input type="email" v-model="email">
    <button @click="alertMyEmail()">Wchodzę</button>
-->
  </div>
</template>

<script>

export default {
  data() {
    return {
      email: '',
      authenticatedUsername: ''
    };
  },
  methods: {
    alertMyEmail() {
      alert(this.email);
    },
    logMeIn() {
      this.authenticatedUsername = this.email;
      this.email = '';
    },
    logMeOut() {
      this.authenticatedUsername = '';
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
</style>
