<template>
  <p>
    <strong>{{ name }}</strong>
    <YummyMealPrice :price="price" />
    <button @click="addToCart">Add to Cart</button>
  </p>
</template>

<script setup>
import { computed } from 'vue'; // Not required. Just for visibility.
import YummyMealPrice from './YummyMealPrice.vue';

const props = defineProps({
  name: String,
  price: Number,
});

const emit = defineEmits(['addTocart']);

const addToCart = () => emit('addToCart', props.name);
const pricePretty = computed(() => `$${props.price.toFixed()}`);
const pricePrettySentence = computed(
  () => `The price of this item is ${pricePretty.value}`
);
</script>

<style scoped></style>
