<template>
  <div>
    <div class="text-center text-4xl">Debt clock</div>
    <div class="text-right text-slate-400">- 借金時計</div>
    <div class="text-center">At 🇯🇵Japan</div>
    
    <DebtCounter :debts="debtNum" />
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import config from "../debt-clock.ts"
import DebtCounter from "./components/DebtCounter.vue"

const { debt } = config;

export default defineComponent({
  components: {
    DebtCounter,
  },
  data() {
    return {
      debt: {
        time: Date.parse(debt.start),
        changeFromMs: debt.debtFromDay / debt.day // 毎日
          / 24 //毎時
          / 60 //毎分
          / 60 //毎秒
          / 1000, //毎ミリ秒
        debt: debt.debt,
      },
      debtNum: 0,
    }
  },
  methods: {
    update(){
      const date = new Date()
      const debt = (date.getTime() - this.debt.time) * this.debt.changeFromMs + this.debt.debt
      this.debtNum = debt
    }
  },
  mounted(){
    setInterval(this.update)
  },
})
</script>

<style scoped>

</style>
