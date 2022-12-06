<script setup lang="ts">
import { computed, ref } from "vue";
import { Show } from "../shared/types";
import Checkout from "./Checkout.vue";
import Payment from "./Payment.vue";

defineProps<{ shows: Show[] }>();
</script>

<template>
  <form class="grid grid-cols-1 md:grid-cols-2">
    <Payment />
    <Checkout :shows="shows" />
  </form>
</template>

<style scoped>
</style>
