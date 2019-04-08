<template>
  <div class="hello">
    <h1>Card {{ caseNumber }} </h1>
    <CardPicture :key="caseNumber + '.1'" v-if="!pickedCard || pickedCard==1" :case="caseNumber" :cardNumber="1" @pickPicture="pick"/>
    <CardPicture :key="caseNumber + '.2'" v-if="!pickedCard || pickedCard==2" :case="caseNumber" :cardNumber="2" @pickPicture="pick"/>
    <span v-if="correctAnswer">GOOD</span>
    <span v-if="!correctAnswer && isSolved">BAD</span>
    <button @mousedown="compare" @mouseup="compare" v-if="isSolved">COMPARE</button>
    <button v-if="isSolved" @click="nextStage">NEXT</button>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import CardPicture from '@/components/CardPicture.vue';

export default Vue.extend({
  name: 'Card',
  components: {
    CardPicture,
  },
  props: {
    caseNumber: Number,
  },
  data() {
    return {
      isSolved: false as Boolean,
      correctAnswer: null as unknown,
      pickedCard: 0 as Number,
    };
  },
  computed: {
    caseData(): Object {
      return require(`../assets/${this.caseNumber}/description.json`)
    }
  },
  methods: {
    pick(cardNo: Number) {
      this.isSolved = true;
      this.pickedCard = cardNo
      cardNo === this.caseData.correct ? this.correctAnswer = false : this.correctAnswer = true
      this.correctAnswer && this.$emit('goodAnswer')
      console.log(cardNo)
    },
    compare() {
      this.pickedCard === 1 ? this.pickedCard = 2 : this.pickedCard = 1 
    },
    nextStage () {
      this.isSolved = false
      this.correctAnswer = null
      this.pickedCard = 0
      this.$emit('nextStage')
    }
  },
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
