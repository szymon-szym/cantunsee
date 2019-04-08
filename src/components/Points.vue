<template>
  <div class="hello">
    <span>points: {{ msg }}</span>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';

export default Vue.extend({
  name: 'Points',
  props: {
    msg: Number,
  },
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
