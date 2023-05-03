<template>
  <div>
    <h1>借金時計</h1>
    {{ debt.changeFromMs }}
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import config from "../debt-clock.ts"

const { debt } = config;

export default defineComponent({
  data() {
    return {
      debt: {
        time: Date.parse(debt.start),
        changeFromMs: debt.debtFromDay / debt.day // 毎日
          / 24 //毎時
          / 60 //毎分
          / 60 //毎秒
          / 1000 //毎ミリ秒
      },
    }
  },
  methods: {
  
  },
})
</script>

<style scoped>

</style>
