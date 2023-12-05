<template>
  <Link href="/">Main Page</Link>&nbsp;
  <Link href="/hello">Show Page</Link>&nbsp;
  <Link href="/listing">Listing</Link>&nbsp;
  <Link href="/listing/create">Create Listing</Link>
  <div>&nbsp;</div>
  <!-- <div>The page is running about {{ timer }} seconds.</div> -->
  <div v-if="flashSuccess" class="success">
    {{ flashSuccess }}
  </div>
  <div>&nbsp;</div>

  <slot>hello</slot>
</template>

<script setup>
import { computed } from 'vue'
import { Link, usePage } from '@inertiajs/vue3'
const page = usePage()
const flashSuccess = computed(() => page.props.flash.success)
</script>

<style scoped>
.success {
  background-color: green;
  color: white;
}
</style>
