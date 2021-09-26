<template>
  <div id="app">
    <!--<img alt="Vue logo" src="./assets/logo.png" /> -->
    <HelloWorld msg="Welcome to Your Vue.js App" />
    <penparnaja /> 
  </div>
</template>

<script>
import Vue from "vue";
// import Employee
// import Employee from "./components/Employee.vue";
// import facultly from './components/faculty.vue';
// import HelloWorld from './components/HelloWorld.vue';
// import Test from './components/Test.vue';
import penparnaja from "./components/penparnaja.vue";

import { BootstrapVue, IconsPlugin } from "bootstrap-vue";
import "bootstrap/dist/css/bootstrap.css";
import "bootstrap-vue/dist/bootstrap-vue.css";

Vue.use(BootstrapVue);
Vue.use(IconsPlugin);
export default {
  name: "App",
  components: {
    // HelloWorld,
    // facultly,
    // Test,
    // Employee,
    penparnaja,
  },
};
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
