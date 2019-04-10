<template>
  <v-app>
    <v-content>
      <div class="hero">
        <img class="logo" alt="Vue logo" src="./assets/logo_vue.png">
        <span class="plus">+</span>
        <img class="logo" alt="IOTAPay logo" src="./assets/logo_iotapay.png">
      </div>
      <h1>Vue and IOTA Pay</h1>
      <h4>IOTA Pay Examples</h4>
      <v-container fluid>
        <BalanceCheck/>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
import BalanceCheck from "./components/BalanceCheck.vue";

export default {
  name: "app",
  components: {
    BalanceCheck
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.hero {
  padding: 20px 20px;
}
.logo {
  height: 75px;
}

.plus {
  font-size: 5em;
}
</style>
