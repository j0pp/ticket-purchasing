<script setup lang="ts">
import { computed, ref } from "vue";
import { Show } from "../shared/types";

const props = defineProps<{ show: Show }>();

const incrementCount = () => {
  props.show.count++;
};

const decrementCount = () => {
  if (props.show.count === 0) return;
  props.show.count--;
};
</script>

<template>
  <li class="flex flex-row bg-indigo-800 rounded-md p-2">
    <div class="flex-grow">
      <h2 class="text-lg">
        {{ show.title
        }}<span class="ml-2 text-sm text-indigo-300"
          >({{ show.location }})</span
        >
      </h2>
      <p class="text-gray-400">{{ show.subtitle }}</p>
    </div>
    <div class="flex flex-col">
      <div class="text-center">${{ show.price.toFixed(2) }}</div>
      <div class="text-center">
        <button @click="decrementCount">
          <i class="bi bi-dash-circle"></i>
        </button>
        {{ show.count }}
        <button @click="incrementCount">
          <i class="bi bi-plus-circle"></i>
        </button>
      </div>
    </div>
  </li>
</template>

<style scoped>
</style>
