<script setup lang="ts">
import { computed, ref } from "vue";
import ShowListItem from "./components/ShowListItem.vue";
import PaymentCheckoutForm from "./components/PaymentCheckoutForm.vue";

const shows = ref([
  {
    id: 1,
    title: "Craig's Crazy Show",
    subtitle: "A crazy show done by DJ Craig.",
    location: "Seattle, WA",
    price: 1,
    count: ref(0),
  },
  {
    id: 2,
    title: "DIPLO at the Tacoma Dome",
    subtitle: "Diplo will be playing at 8:00PM on Saturday, December 10th.",
    location: "Tacoma, WA",
    price: 300,
    count: ref(0),
  },
  {
    id: 3,
    title: "Local DJ Mixes Poorly",
    subtitle: "Your local DJ is here to play some crazy mashups in the club!",
    location: "Seattle, WA",
    price: 100,
    count: ref(0),
  },
  {
    id: 4,
    title: "Taylor Swift",
    subtitle: "TicketMaster really messed up and now this concert is $4000.00!",
    location: "New York City, NY",
    price: 4000,
    count: ref(0),
  },
  {
    id: 5,
    title: "Yung Gravy",
    subtitle:
      "Yung Gravy is coming to Portland! Buy these tickets before they sell out.",
    location: "Portland, OR",
    price: 150,
    count: ref(0),
  },
  {
    id: 6,
    title: "PSY",
    subtitle: "Oppa Gangnam Style...",
    location: "Seoul, KR",
    price: 600,
    count: ref(0),
  },
]);

const totalCount = computed(() => {
  return shows.value.reduce((prev, show) => {
    return prev + show.count;
  }, 0);
});
</script>

<template>
  <header class="flex row">
    <nav class="flex-grow">
      <h1 class="text-xl inline" role="button">
        <a href="/">Ticket Purchasing Demo</a>
      </h1>
    </nav>
    <div>
      <span class="mr-2">{{ totalCount }}</span>
      <i class="bi bi-cart2 text-xl"></i>
    </div>
  </header>
  <div class="mt-8">
    <h2 class="font-bold mb-2">
      SHOWS <i class="bi bi-calendar4-event ml-1"></i>
    </h2>
    <ul class="grid grid-cols-1 md:grid-cols-2 gap-x-5 gap-y-3">
      <ShowListItem
        v-for="show in shows"
        :key="show.id"
        :show="show"
      ></ShowListItem>
    </ul>
  </div>
  <div class="mt-8">
    <PaymentCheckoutForm :shows="shows" />
  </div>
</template>

<style scoped>
</style>
