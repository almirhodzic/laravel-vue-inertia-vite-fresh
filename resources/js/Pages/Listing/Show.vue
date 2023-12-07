<template>
  <div class="flex flex-col-reverse md:grid md:grid-cols-12 gap-4">
    <Box class="md:col-span-7 flex items-center w-full">
      <div class="w-full text-center">Image</div>
    </Box>
    <div class="md:col-span-5 flex flex-col gap-4">
      <Box>
        <template #header>
          Basic Info
        </template>
        <Price :price="listing.price" class="text-2xl font-bold" />
        <LisitingSpace :listing="listing" class="text-lg" />
        <ListingAddress :listing="listing" class="text-gray-500" />
      </Box>
      <Box>
        <template #header>
          Monthly payment
        </template>
        <div>
          <label>Interest rate ({{ interestRate }}%)</label>
          <input v-model.number="interestRate" type="range" min="0.1" max="30" step="0.1" class="form-range" />

          <label>Duration ({{ duration }} years)</label>
          <input v-model.number="duration" type="range" min="3" max="35" step="1" class="form-range" />

          <div class="text-gray-600 dark:text-gray-300 mt-2">
            <div class="text-gray-500 mb-1">Your monthly payment</div>
            <Price :price="monthlyPayment" class="text-3xl" />
          </div>
        </div>
      </Box>
    </div>
  </div>
</template>

<script setup>
import ListingAddress from '@/Components/ListingAddress.vue'
import LisitingSpace from '@/Components/LisitingSpace.vue'
import Price from '@/Components/Price.vue'
import Box from '@/Components/UI/Box.vue'

import { ref } from 'vue'
import { useMonthlyPayment } from '@/Composables/useMonthlyPayment'

const interestRate = ref(2.5)
const duration = ref(25)

const props = defineProps({
    listing: {
        type: Object,
        required: true,
    },
})

const { monthlyPayment } = useMonthlyPayment(props.listing.price, interestRate, duration)
</script>