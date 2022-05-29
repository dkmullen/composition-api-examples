<template>
  <div>
    <h2>{{ user.name }}</h2>
    <h2>{{ user.age }}</h2>
    <h2>{{ userName }}</h2>
    <button @click="changeSomething">Change</button>
    <hr />
    <p>{{ fullName }}</p>
    <input type="text" placeholder="First Name" v-model="firstName" />
    <input type="text" placeholder="Last Name" v-model="lastName" />
  </div>
</template>

<script setup>
/* Same as App2 but with script setup, a simplified syntax */

import { ref, reactive, computed, watch } from 'vue';

const userName = ref('dkmullen');
const user = reactive({
  name: 'Joker',
  age: 18,
});
const firstName = ref('');
const lastName = ref('');

// Computed props are read-only; Can't set it directly elsewhere
const fullName = computed(() => {
  return firstName.value + ' ' + lastName.value;
});

// Watch returns new and old values; can use one item or an array
watch([firstName, lastName], function (newValuez, oldValuez) {
  console.log(newValuez[0], oldValuez[0]);
  console.log(newValuez[1], oldValuez[1]);
});

setTimeout(() => {
  (user.name = 'Joker Davis'), (user.age = 19), (userName.value = 'joker');
}, 3000);

function changeSomething() {
  user.age -= 1;
}
</script>

<style></style>
