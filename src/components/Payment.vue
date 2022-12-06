<script setup lang="ts">
import { computed, ref, watchEffect } from "vue";
import { Show } from "../shared/types";

// const props = defineProps<{ shows: Show[] }>();
</script>

<template>
  <div class="flex flex-col p-3">
    <h2 class="font-bold">
      PAYMENT <i class="bi bi-credit-card-2-front ml-1"></i>
    </h2>
    <h3 class="mt-1">Add Credit/Debit Card Information</h3>
    <fieldset>
      <div>
        <input
          type="radio"
          id="cardTypeChoice1"
          name="cardType"
          autocomplete="cc-type"
          value="visa"
        />
        <label for="cardTypeChoice1">
          <img
            src="../assets/visa.svg"
            class="w-10 inline ml-1"
            alt="Visa Card"
          />
        </label>

        <input
          class="ml-2"
          type="radio"
          id="cardTypeChoice2"
          name="cardType"
          value="mastercard"
        />
        <label for="cardTypeChoice2"
          ><img
            src="../assets/mastercard.svg"
            class="w-10 inline ml-2"
            alt="Master Card"
        /></label>
      </div>
    </fieldset>
    <label for="card-name">Card Holder</label>
    <input
      class="rounded p-1"
      id="card-name"
      type="text"
      inputmode="text"
      pattern="[0-9\s]{13,19}"
      autocomplete="cc-name"
      maxlength="19"
      placeholder="John Doe"
    />
    <label class="mt-2" for="card-number">Card Number</label>
    <input
      class="rounded p-1"
      id="card-number"
      v-model="cardNumber"
      type="tel"
      inputmode="numeric"
      pattern="[0-9\s]{13,19}"
      autocomplete="cc-number"
      maxlength="19"
      placeholder="#### #### #### ####"
    />
    <label class="mt-2" for="security-code">Security Code</label>
    <input
      class="rounded p-1"
      id="security-code"
      v-model="cardCSC"
      type="tel"
      inputmode="numeric"
      pattern="[0-9\s]{3}"
      autocomplete="cc-csc"
      maxlength="3"
      placeholder="###"
    />
    <label class="mt-2" for="card-exp">Expiration Date</label>
    <input
      class="rounded p-1"
      id="security-code"
      type="text"
      inputmode="numeric"
      pattern="[0-9\s]{3}"
      autocomplete="cc-exp"
      maxlength="7"
      placeholder="MM/YYYY"
    />
    <button type="button" class="bg-sky-500 my-4 mx-16 p-3 rounded">
      Or, use PayPal
      <i class="bi bi-paypal"></i>
    </button>
  </div>
</template>

<style scoped>
</style>