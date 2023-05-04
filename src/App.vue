<template>
  <div>
    <div class="text-center text-4xl">Debt clock</div>
    <div class="text-right text-slate-400 pr-1">- 借金時計</div>
    <div class="text-center">{{ location }}</div>
    
    <DebtCounter :debts="debtNum" />
    <div>
      <div class="text-xl">一人当たり({{ population.view }}):</div>
      <PersonDebt :debts="debtNum" :population="population" />
    </div>
    <div>
      <ul>
        <li>Souce Code: <a class="text-blue-500" href="https://github.com/nakasyou/debt-clock">https://github.com/nakasyou/debt-clock</a></li>
      </ul>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import config from "../debt-clock.ts"
import DebtCounter from "./components/DebtCounter.vue"
import PersonDebt from "./components/PersonDebt.vue"

const { debt, population, location } = config;

export default defineComponent({
  components: {
    DebtCounter,
    PersonDebt,
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
      population,
      location,
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
