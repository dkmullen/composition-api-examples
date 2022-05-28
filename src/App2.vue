<template>
  <div>
    <h2>{{ user.name }}</h2>
    <h2>{{ user.age }}</h2>
    <h2>{{ userName }}</h2>
    <button @click="changeSomething">Change</button>
  </div>
</template>

<script>
import { ref, reactive } from '@vue/reactivity';
export default {
  setup() {
    // ref is for any type, reactive is for objects;
    const userName = ref('dkmullen');
    const user = reactive({
      name: 'Dennis',
      age: 57,
    });

    setTimeout(() => {
      (user.name = 'Dennis Mullen'),
        (user.age = 58),
        (userName.value = 'dkmullen777');
    }, 3000);

    function changeSomething() {
      this.user.age -= 1;
    }

    return { user, userName, changeSomething };
  },
};
</script>

<style></style>
