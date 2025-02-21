<script setup>
import Dice from "./components/Dice.vue";
import RollButton from "./components/RollButton.vue";
import DeleteHistory from "./components/DeleteHistory.vue"
import { ref, computed } from 'vue';

let diceHistory = ref([]);

const TYPES = ["PF", "MC", "TC", "DF", "DR"]
let choosenType = ref("")

const recentDices = computed(() => {
  return diceHistory.value || [];
});

function addDiceRoll() {
  const newRoll = [[Math.floor(Math.random() * 6) + 1, choosenType], [Math.floor(Math.random() * 6) + 1, choosenType]];
  diceHistory.value.unshift(newRoll);
  choosenType = ref("")
}

function deleteHistory() {
  diceHistory.value = [];
}
</script>

<template>
  <h1>Dé virtuel</h1>
  <div class="container">
    <div v-for="(hist, index) in recentDices" :key="index" class="histLine">
      <Dice :num="hist[0][0]" v-bind:isLatest="index === 0"/>
      <Dice :num="hist[1][0]" v-bind:isLatest="index === 0"/>
    </div>
  </div>
  <div class="toolbar">
    <div class="column">
      <p v-for="type in TYPES.slice(0, 3)" :style="`text-align:right; color: ${choosenType===type ? 'var(--color-heading)' : 'var(--color-text)'}`" :key="type" id="typeBtn" @click="choosenType = type!==choosenType ? type : ''">{{ type }}</p>
    </div>
    <RollButton @click="addDiceRoll" id="roller" v-bind:active="choosenType" />
    <div class="column">
      <p v-for="type in TYPES.slice(3)" :key="type" id="typeBtn" :style="`text-align:right; color: ${choosenType===type ? 'var(--color-heading)' : 'var(--color-text)'}`" @click="choosenType = type!==choosenType ? type : ''">{{ type }}</p>
    </div>
  </div>
  <br><DeleteHistory @click="deleteHistory" v-bind:visible="diceHistory.length" />
</template>

<style scoped>
.toolbar {
  position: sticky;
  margin: 30px 0;
  padding: 20px 0 30px 0;
  backdrop-filter: blur(5px) contrast(0.5) brightness(var(--toolbar-lowered-brightness));;
  bottom: 0;
  display: flex;
  justify-content: center;
  #typeBtn {
    font-size: 17px
  }
}

.histLine {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  padding: 15px 0;
}
</style>
