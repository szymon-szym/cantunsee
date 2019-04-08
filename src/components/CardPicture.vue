<template>
  <div class="testCard">
    <img @click="pickCard" :src="imgPath" alt="Illustration to the test">
  </div>
</template>

<script lang="ts">
import Vue from 'vue';

export default Vue.extend({
  name: 'CardPicture',
  props: {
    cardNumber: Number,
    case: Number,
  },
  data() {
    return {
      // imgPath: `@/assets/1/${this.cardNumber}.png`
    }
  },
  computed: {
    imgPath() :String {
      return require(`../assets/${this.case}/${this.cardNumber}.jpg`)
    }
  },
  methods: {
    pickCard() {
      this.$emit('pickPicture', this.cardNumber)
    },
  }
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
