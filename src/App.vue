<script setup>
import Dice from "./components/Dice.vue";
import RollButton from "./components/RollButton.vue";
import { ref, computed } from 'vue';

let dicesHistory = ref([]);

const recentDices = computed(() => {
  return dicesHistory.value.slice(0, 5);
});

function addDiceRoll() {
  const newRoll = [Math.floor(Math.random() * 6) + 1, Math.floor(Math.random() * 6) + 1, true];
  dicesHistory.value.unshift(newRoll);
  if (dicesHistory.value.length > 5) {
    dicesHistory.value.pop()
  }
}
</script>

<template>
  <h1>Dé virtuel</h1>
  <div class="container">
    <div v-for="(hist, index) in recentDices" :key="index" class="histLine">
      <Dice :num="hist[0]" v-bind:isLatest="index === 0"/>
      <Dice :num="hist[1]" v-bind:isLatest="index === 0"/>
    </div>
  </div>
  <RollButton @click="addDiceRoll" id="roller" />
</template>

<style scoped>
#roller {
  position: sticky;
  bottom: 0;
  left: 50%;
  transform: translate(-50%, -100%);

}

.histLine {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  padding: 15px 0;
}
</style>
