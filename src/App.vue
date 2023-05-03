<template>
  <div>
    <h1>借金時計</h1>
    {{ config.debt.start }}
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import config from "../debt-clock.json" assert { type: "json" }

export default defineComponent({
  
})
</script>

<style scoped>

</style>
