<script setup lang="ts">
import { computed, ref } from "vue";
import ShowListItem from "./components/ShowListItem.vue";
import PaymentCard from "./components/PaymentCard.vue";

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
    title: "Craig's Crazy Show",
    subtitle: "A crazy show done by DJ Craig.",
    location: "Seattle, WA",
    price: 300,
    count: ref(0),
  },
  {
    id: 3,
    title: "Craig's Crazy Show",
    subtitle: "A crazy show done by DJ Craig.",
    location: "Seattle, WA",
    price: 300,
    count: ref(0),
  },
  {
    id: 4,
    title: "Craig's Crazy Show",
    subtitle: "A crazy show done by DJ Craig.",
    location: "Seattle, WA",
    price: 300,
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
    <h2 class="font-bold">SHOWS</h2>
    <ul>
      <ShowListItem
        v-for="show in shows"
        :key="show.id"
        :show="show"
      ></ShowListItem>
    </ul>
  </div>
  <div class="mt-8">
    <PaymentCard></PaymentCard>
  </div>
</template>

<style scoped>
</style>
