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
  <div>
    {{ debtsPre(debts).join(" ") }}
  </div>
</template>
