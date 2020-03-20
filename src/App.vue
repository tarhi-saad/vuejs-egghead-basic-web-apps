<template>
  <v-app id="app">
    <Card/>
    <List/>
  </v-app>
</template>

<script>
import List from "./components/List";
import Card from "./components/Card";

export default {
  name: "App",
  components: {
    List,
    Card
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
}
</style>
