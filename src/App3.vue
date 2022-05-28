<template>
  <div>
    <h2>{{ user.name }}</h2>
    <h2>{{ user.age }}</h2>
    <h2>{{ userName }}</h2>
    <button @click="changeSomething">Change</button>
  </div>
</template>

<script setup>
/* Same as App2 but with script setup, a simplified syntax */

import { ref, reactive } from '@vue/reactivity';

const userName = ref('dkmullen');
const user = reactive({
  name: 'Joker',
  age: 18,
});

setTimeout(() => {
  (user.name = 'Joker Davis'), (user.age = 19), (userName.value = 'joker');
}, 3000);

function changeSomething() {
  user.age -= 1;
}
</script>

<style></style>
