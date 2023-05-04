<script setup lang="ts">
const props = defineProps<{
  debts: number
}>()

const debtsPre = (debts: number): number[] => {
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
.unit{
  font-size: 2em;
}
.num{
  font-size: 4em;
}
.units{
  display: flex;
  justify-content: center;
}
</style>
