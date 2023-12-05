<template>
  <form @submit.prevent="form.patch(`/listing/${props.listing.id}`)">
    <div>
      <div>
        <label>Beds</label>
        <input id="beds" v-model.number="form.beds" type="number" />
        <div v-if="form.errors.beds" class="error">{{ form.errors.beds }}</div>
      </div>

      <div>
        <label>Baths</label>
        <input id="baths" v-model.number="form.baths" type="number" />
        <div v-if="form.errors.baths" class="error">{{ form.errors.baths }}</div>
      </div>

      <div>
        <label>Area</label>
        <input id="area" v-model="form.area" type="number" />
        <div v-if="form.errors.area" class="error">{{ form.errors.area }}</div>
      </div>

      <div>
        <label>City</label>
        <input v-model="form.city" type="text" />
        <div v-if="form.errors.city" class="error">{{ form.errors.city }}</div>
      </div>

      <div>
        <label>Post Code</label>
        <input id="code" v-model.number="form.code" type="text" />
        <div v-if="form.errors.code" class="error">{{ form.errors.code }}</div>
      </div>

      <div>
        <label>Street</label>
        <input id="street" v-model="form.street" type="text" />
        <div v-if="form.errors.street" class="error">{{ form.errors.street }}</div>
      </div>

      <div>
        <label>Street Nr</label>
        <input id="street_nr" v-model="form.street_nr" type="text" />
        <div v-if="form.errors.street_nr" class="error">{{ form.errors.street_nr }}</div>
      </div>

      <div>
        <label>Price</label>
        <input id="price" v-model.number="form.price" type="number" />
        <div v-if="form.errors.price" class="error">{{ form.errors.price }}</div>
      </div>

      <div>&nbsp;</div>

      <div>
        <button type="submit" :disabled="form.processing">Update</button>
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
label {
  margin-right: 2em;
  width: 75px;
  display: inline-block;
}

div {
  padding: 2px
}
.error {
  background-color: red;
  color: white;
}
</style>