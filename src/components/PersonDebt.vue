<script setup lang="ts">
const props = defineProps<{
  debts: number
  population: {population: number, view: string}
}>()

const debtsPre = (debts: number): number[] => {
  debts /= population.population;
  alert(debts,population.population)
  let result = "";
  let i=0;
  for(const char of Array.from(String(Math.floor(debts))).reverse()){
    result = char + result;
    if(i % 4 === 3){
      result = "," + result;
    }
    i++;
  }
  if(result[0] === ",")
    result = result.slice(1);
  return result.split(",")
}
</script>
<template>
  <div class="units">
    <div v-for="(unit, index) in debtsPre(debts)" :key="index">
      <span class="num">{{ unit }}</span>
      <span class="unit">{{ "兆億万円"[index] }}</span>
    </div>
  </div>
</template>
<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Roboto+Mono:wght@300&display=swap');

.unit{
  font-size: 1.5em;
}
.num{
  font-size: 3em;
  font-family: 'Roboto Mono', monospace;
}
.units{
  display: flex;
  justify-content: center;
}
</style>
