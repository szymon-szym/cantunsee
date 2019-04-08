<template>
  <div class="hello">
    <button @click="restart">RESTART</button>
    <div v-if="stage < 10" class="game">
      <h1>Main</h1>
      <h1>Stage {{ stage }}</h1>
      <Points :msg="points"/>
      <Card @nextStage="nextStage" @goodAnswer="addPoints" :caseNumber="stage"/>
      <MainViewProgress/>
    </div>
    <div class="endGame">
      <h1 v-if="stage >= 10">THE END</h1>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import Card from './Card.vue';
import Points from './Points.vue';
import MainViewProgress from '@/components/MainViewProgress.vue';

export default Vue.extend({
  name: 'MainView',
  components: {
    Card,
    Points,
    MainViewProgress,
  },
  props: {
    msg: String,
  },
  data() {
    return {
      stage: 1,
      points: 0 as number,
    }
  },
  methods: {
    nextStage() {
      this.stage += 1
      localStorage.stage = this.stage
    },
    restart() {
      this.stage = 1
      this.points = 0
      localStorage.stage = 1
      localStorage.points = 0
    },
    addPoints() {
      this.points += Number(10)
      localStorage.points = this.points
    },
  },
  mounted() {
    localStorage.points && (this.points = Number(localStorage.points)) 
    localStorage.stage && (this.stage = Number(localStorage.stage)) 

  }
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
