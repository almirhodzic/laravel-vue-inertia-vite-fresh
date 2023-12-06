<template>
  <form @submit.prevent="form.patch(route('listing.update', props.listing.id))">
    <div class="grid grid-cols-6 gap-4">
      <div class="col-span-2">
        <label class="form-label">Beds</label>
        <input id="beds" v-model.number="form.beds" type="number" class="form-input-text" />
        <div v-if="form.errors.beds" class="form-bag-error">{{ form.errors.beds }}</div>
      </div>

      <div class="col-span-2">
        <label class="form-label">Baths</label>
        <input id="baths" v-model.number="form.baths" type="number" class="form-input-text" />
        <div v-if="form.errors.baths" class="form-bag-error">{{ form.errors.baths }}</div>
      </div>

      <div class="col-span-2">
        <label class="form-label">Area</label>
        <input id="area" v-model="form.area" type="number" class="form-input-text" />
        <div v-if="form.errors.area" class="form-bag-error">{{ form.errors.area }}</div>
      </div>

      <div class="col-span-4">
        <label class="form-label">City</label>
        <input v-model="form.city" type="text" class="form-input-text" />
        <div v-if="form.errors.city" class="form-bag-error">{{ form.errors.city }}</div>
      </div>

      <div class="col-span-2">
        <label class="form-label">Post Code</label>
        <input id="code" v-model.number="form.code" type="text" class="form-input-text" />
        <div v-if="form.errors.code" class="form-bag-error">{{ form.errors.code }}</div>
      </div>

      <div class="col-span-4">
        <label class="form-label">Street</label>
        <input id="street" v-model="form.street" type="text" class="form-input-text" />
        <div v-if="form.errors.street" class="form-bag-error">{{ form.errors.street }}</div>
      </div>

      <div class="col-span-2">
        <label class="form-label">Street Nr</label>
        <input id="street_nr" v-model="form.street_nr" type="text" class="form-input-text" />
        <div v-if="form.errors.street_nr" class="form-bag-error">{{ form.errors.street_nr }}</div>
      </div>

      <div class="col-span-6">
        <label class="form-label">Price</label>
        <input id="price" v-model.number="form.price" type="number" class="form-input-text" />
        <div v-if="form.errors.price" class="form-bag-error">{{ form.errors.price }}</div>
      </div>

      <div class="col-span-6 mt-4">
        <button type="submit" :disabled="form.processing" class="form-button-create">Update Listing</button>
      </div>
    </div>
  </form>
</template>

<script setup>
import { useForm } from '@inertiajs/vue3'

const props = defineProps({
    listing: Object,
})

const form = useForm({
    beds: props.listing.beds,
    baths: props.listing.baths,
    area: props.listing.area,
    city: props.listing.city,
    code: props.listing.code,
    street: props.listing.street,
    street_nr: props.listing.street_nr,
    price: props.listing.price,
})
</script>

<style scoped>

</style>