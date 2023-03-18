<template>
  <span>
    {{ pricePretty }}
  </span>
</template>

<script>
import { computed, inject, ref } from 'vue';
export default {
  props: { price: String },

  setup(props, { emit }) {
    const currencySymbol = inject('currencySymbol', ref('$'));
    const pricePretty = computed(
      () => `${currencySymbol.value}${props.price.toFixed()}`
    );

    return { pricePretty };
  },
};
</script>

<style scoped></style>
