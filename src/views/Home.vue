<script setup lang="ts">
import {  ref } from 'vue'
import 'yatori-checkout'

const merchantWalletAddress = ref('')
const merchantItemAmount = ref('')
const isQrReady = ref(false)
const qrKey = ref(0)

const displayConfirmation = (event: any) => {
  console.log('Payment confirmed!', event.detail)
  window.removeEventListener('yatori-confirmed', displayConfirmation)
}

const submitMerchantDetails = () => {
  if (merchantItemAmount.value && merchantWalletAddress.value) {
    window.addEventListener('yatori-confirmed', displayConfirmation)
    isQrReady.value = true
    qrKey.value++
    console.log('QR CODE READY FOR PAYMENT')
  }
}
</script>

<template>
  <div class="container">
    <h1>YATORI CHECKOUT DEMO</h1>

    <form @submit.prevent="submitMerchantDetails" class="form-wrapper">
      <input v-model="merchantWalletAddress" />
      <input v-model="merchantItemAmount" />
      <button type="submit">Generate Qr code</button>
    </form>

    <yatori-checkout
      v-if="isQrReady"
      :key="qrKey"
      :wallet="merchantWalletAddress"
      :amount="merchantItemAmount"
    />
  </div>
</template>

<style lang="css">
body {
  background-color: #353535;
}

.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: #353535;
  color: #ffff;
}

.form-wrapper {
  display: flex;
  flex-direction: column;
  gap: 15px;
  min-width: 40%;
}
</style>
