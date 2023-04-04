<script setup lang="ts">
import { onMounted } from 'vue'
import PaystackPop from '@paystack/inline-js';

onMounted(async () => {
  const paystackPop = new PaystackPop()

  await paystackPop.paymentRequest({
    key: 'pk_domain_xxxxx',
    email: 'CUSTOMER_EMAIL',
    amount: 10000,
    currency: 'NGN',
    ref: 'YOUR_REFERENCE',
    container: 'paystack-apple-pay',
    loadPaystackCheckButton: 'paystack-other-channels',
    style: {
      theme: 'dark',
      applePay: {
        margin: '10px',
        padding: '10px',
        width: '100%',
        borderRadius: '5px',
        type: 'pay',
        locale: 'en'
      }
    },
    onSuccess(response: any) {
      // do stuff
      console.log(response)
    },
    onError() {
      // do stuff
    },
    onCancel() {
      // do stuff
    },
    onElementsMount(elements: any) {
      console.log(elements)
      // { applePay: true } or null
    }
  })
})
</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />
    </div>
  </header>

  <main>
    <div id="paystack-apple-pay"></div>
    <button id="paystack-other-channels">More payment options</button>
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
