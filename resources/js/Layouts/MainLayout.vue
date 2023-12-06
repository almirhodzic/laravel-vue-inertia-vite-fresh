<template>
  <header class="header-element">
    <div class="container mx-auto">
      <nav class="p-4 flex items-center justify-between">
        <div class="text-lg font-medium">
          <Link :href="route('listing.index')">Listings</Link>
        </div>
        <div class="page-title">
          <Link :href="route('listing.index')">LaraZillow</Link>
        </div>
        <div>
          <Link :href="route('listing.create')" class="form-button-create py-2.5">+ New Listing</Link>
        </div>
      </nav>
    </div>
  </header>

  <main class="container mx-auto p-4">
    <div v-if="flashSuccess" class="form-bag-success">
      {{ flashSuccess }}
    </div>
    <slot>Default</slot>
  </main>
</template>

<script setup>
import { computed } from 'vue'
import { Link, usePage } from '@inertiajs/vue3'
const page = usePage()
const flashSuccess = computed(() => page.props.flash.success)
</script>
