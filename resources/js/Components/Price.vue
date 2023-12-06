<template>
  <span>
    {{ formattedPrice }}
  </span>
</template>

<script setup>
import { computed } from 'vue'

const props = defineProps({
    price: [Number, String],
})
const formattedPrice = computed(() => {
    return new Intl.NumberFormat('de-CH', { 
        style: 'currency', 
        currency: 'CHF',
        maximumFractionDigits: 0, 
    }).format(props.price)
})
</script>

<style lang="scss" scoped>

</style>