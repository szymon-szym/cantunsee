<template>
  <div id="app">
    <MainView msg="Props for main view"/>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import HelloWorld from './components/HelloWorld.vue';
import MainView from './components/MainView.vue';

export default Vue.extend({
  name: 'app',
  components: {
    HelloWorld,
    MainView,
  },
});
</script>

<style>
#app {
  font-family: 'Roboto', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
