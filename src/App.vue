<template>
  <section class="container">
    <h2>{{ userName }}</h2>
    <h3>{{ age }}</h3>
  </section>
  <section class="container">
    <App2 :message="'Hey now!'" @myMessage="showMsg" />
  </section>
  <section class="container">
    <App3 />
  </section>
</template>

<script>
import { ref } from 'vue';
import App2 from './App2.vue';
import App3 from './App3.vue';

export default {
  components: { App2, App3 },
  setup() {
    const uName = ref('Max');
    const age = ref(31);
    setTimeout(() => {
      uName.value = 'Maximilian';
    }, 2000);
    function showMsg(msg) {
      console.log(msg);
    }
    return {
      userName: uName,
      age,
      showMsg,
    };
  },
  // data() {
  //   return {
  //     userName: 'Maximilian',
  //   };
  // },
};
</script>

<style>
* {
  box-sizing: border-box;
}

html {
  font-family: sans-serif;
}

body {
  margin: 0;
}

.container {
  margin: 3rem auto;
  max-width: 30rem;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 1rem;
  text-align: center;
}
</style>
