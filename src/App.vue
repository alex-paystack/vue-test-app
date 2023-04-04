<script setup lang="ts">
import PaystackPop from '@paystack/inline-js'

async function payWithPaystack() {
  const paystackPop = new PaystackPop()

  await paystackPop.checkout({
    key: 'pk_live_9ad8c35d24534def2eaa1510152899a07de9e706',
    email: 'test@gamil.com',
    amount: 10000
  })
}
</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />
    <div class="wrapper">
      <HelloWorld msg="You did it!" />
    </div>
  </header>

  <main>
    <button @click="payWithPaystack">Pay Me Money</button>
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
