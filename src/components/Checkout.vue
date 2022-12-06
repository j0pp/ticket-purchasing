<script setup lang="ts">
import { computed, ref, watchEffect } from "vue";
import { Show } from "../shared/types";

const props = defineProps<{ shows: Show[] }>();

const TAX_RATE = 10.1;
const SERVICE_FEE = 12;

const showCart = computed(() => {
  return props.shows.filter((show) => show.count > 0);
});

const hasItems = computed(() => {
  return showCart.value.length > 0;
});

const subTotal = computed(() => {
  return showCart.value.reduce((total, show) => {
    return total + show.price * show.count;
  }, 0);
});

const tax = computed(() => {
  return (subTotal.value * TAX_RATE) / 100;
});

const total = computed(() => {
  return subTotal.value + tax.value + SERVICE_FEE;
});
</script>

<template>
  <div class="w-1/2 p-3">
    <h2 class="font-bold">CHECKOUT <i class="bi bi-cart2 text-xl ml-2"></i></h2>
    <div class="flex flex-col" v-if="hasItems">
      <div class="mt-3">
        <h3 class="text-xl font-bold">Tickets</h3>
        <ul>
          <li v-for="show in showCart" :key="show.id" class="">
            <span>{{ show.title }} (Qty. {{ show.count }})</span>
            <span class="float-right"
              >${{ (show.price * show.count).toFixed(2) }}</span
            >
          </li>
        </ul>
      </div>
      <div class="mt-3">
        <h3 class="text-xl font-bold">Fees</h3>
        <ul>
          <li>
            <span>Service Fee</span>
            <span class="float-right">$12.00</span>
          </li>
          <li>
            <span>Tax ({{ TAX_RATE }}%)</span>
            <span class="float-right">${{ tax.toFixed(2) }}</span>
          </li>
        </ul>
      </div>

      <div class="mt-3 text-xl font-bold">
        <h3 class="grow inline">TOTAL</h3>
        <span class="float-right">${{ total.toFixed(2) }}</span>
      </div>

      <div class="mt-3">
        <h3 class="font-bold">Notes from Seller</h3>
        <p>
          Proof of at least one dose of COVID-19 vaccination for ages 5 to 11
          and guests ages 12 and up will be required to show proof of two
          COVID-19 vaccine doses.
        </p>
      </div>
      <button class="bg-indigo-800 mt-3 py-3 px-12 rounded-lg">
        Place Order
      </button>
    </div>
    <div class="text-center w-96 mx-auto py-4" v-else>
      Please add some tickets to your cart to checkout!
    </div>
  </div>
</template>

<style scoped>
</style>