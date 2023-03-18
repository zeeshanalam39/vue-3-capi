<script>
import YummyMeal from './components/YummyMeal.vue';
import { ref, reactive, watch, provide, onMounted } from 'vue';

export default {
  components: { YummyMeal },

  setup() {
    const currencySymbol = ref('$');
    provide('currencySymbol', currencySymbol);
    const name = ref('The Snazzy Burger');
    const meal = reactive({ name: 'Hamburger', price: 5 });
    const meals = reactive([
      { name: 'Hamburger', price: 5 },
      { name: 'Cheese Burger', price: 4 },
      { name: 'Beef urger', price: 7 },
      { name: 'Fries', price: 3 },
    ]);
    const cart = reactive([]);

    const placeOrder = () => alert('Order placed');
    const addItemToCart = (item) => cart.push(item);

    watch(
      () => [...cart],
      (newValue, oldValue) => {
        console.log(newValue, oldValue);
      }
    );

    onMounted(() => console.log('onMounted'));

    return { name, meal, meals, placeOrder, addItemToCart,currencySymbol };
  },
};
</script>

<template>
  <h1>{{ name }}</h1>
  <input type="text" v-model="name" />
  <button @click="placeOrder">Place order</button>
  <YummyMeal
    v-for="meal in meals"
    :name="meal.name"
    :price="meal.price"
    @addToCart="addItemToCart"
  />
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
