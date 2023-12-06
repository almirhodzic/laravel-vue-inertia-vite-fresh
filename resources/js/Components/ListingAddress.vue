<template>
  <span>
    {{ listing.street }}  {{ listing.street_nr }}, 
    {{ listing.city }}
  </span>
</template>

<script setup>
defineProps({
    listing: {
        type: Object,
        required: true,
    },
})
</script>

<style lang="scss" scoped>

</style>