<script setup lang="ts">
const props = defineProps<{
  debts: number
}>()
</script>
<template>
<div>
{{ debts }}
</div>
</template>
