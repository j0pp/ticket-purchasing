<script setup lang="ts">
import { ref } from "vue";
const cardNumber = ref(null);
</script>

<template>
  <div class="">
    <form class="flex flex-row">
      <div class="w-1/2 flex flex-col p-3">
        <h2 class="font-bold">PAYMENT</h2>
        <h3 class="">Add Credit/Debit Card Information</h3>
        <fieldset>
          <div>
            <input
              type="radio"
              id="cardTypeChoice1"
              name="cardType"
              autocomplete="cc-type"
              value="visa"
            />
            <label for="cardTypeChoice1">Visa</label>

            <input
              type="radio"
              id="cardTypeChoice2"
              name="cardType"
              value="mastercard"
            />
            <label for="cardTypeChoice2">Master Card</label>
          </div>
        </fieldset>
        <label for="card-name">Card Holder</label>
        <input
          class="rounded p-1 ml-2"
          id="card-name"
          type="text"
          inputmode="text"
          pattern="[0-9\s]{13,19}"
          autocomplete="cc-name"
          maxlength="19"
          placeholder="John Doe"
        />
        <label for="card-number">Card Number</label>
        <input
          class="rounded p-1 ml-2"
          id="card-number"
          v-model="cardNumber"
          type="tel"
          inputmode="numeric"
          pattern="[0-9\s]{13,19}"
          autocomplete="cc-number"
          maxlength="19"
          placeholder="#### #### #### ####"
        />
        <label for="security-code">Security Code</label>
        <input
          class="rounded p-1 ml-2"
          id="security-code"
          v-model="cardCSC"
          type="tel"
          inputmode="numeric"
          pattern="[0-9\s]{3}"
          autocomplete="cc-csc"
          maxlength="3"
          placeholder="###"
        />
        <label for="card-exp">Expiration Date</label>
        <input
          class="rounded p-1 ml-2"
          id="security-code"
          type="text"
          inputmode="numeric"
          pattern="[0-9\s]{3}"
          autocomplete="cc-exp"
          maxlength="7"
          placeholder="MM/YYYY"
        />
      </div>
      <div class="w-1/2 p-3">
        <h2 class="font-bold">CHECKOUT</h2>
        <div class="flex flex-col">
          <div class="mt-3">
            <h3 class="text-xl font-bold">Tickets</h3>
            <ul>
              <li class="">
                <span>Craigs Crazy Show (Qty. 3)</span>
                <span class="float-right">$900.00</span>
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
                <span>Tax (10.1%)</span>
                <span class="float-right">$15.42</span>
              </li>
            </ul>
          </div>

          <div class="mt-3 text-xl font-bold">
            <h3 class="grow inline">TOTAL</h3>
            <span class="float-right">$930.23</span>
          </div>

          <div class="mt-3">
            <h3>Notes from Seller</h3>
            <p>
              Proof of at least one dose of COVID-19 vaccination for ages 5 to
              11 and guests ages 12 and up will be required to show proof of two
              COVID-19 vaccine doses.
            </p>
          </div>
          <button class="bg-indigo-800 mt-3 py-3 px-12 rounded-lg">
            Place Order
          </button>
        </div>
      </div>
    </form>
  </div>
</template>

<style scoped>
</style>
