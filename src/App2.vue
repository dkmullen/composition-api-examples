<template>
  <div>
    <h2>{{ user.name }}</h2>
    <h2>{{ user.age }}</h2>
    <h2>{{ userName }}</h2>
    <button @click="changeSomething">Change</button>
    <hr />
    <p>{{ fullName }}</p>
    <input type="text" placeholder="First Name" @input="setFirstName" />
    <input type="text" placeholder="Last Name" v-model="lastName" />
  </div>
</template>

<script>
import { ref, reactive, computed, watch, onMounted } from 'vue';
export default {
  props: ['message'],
  // props, context get passed automatically to setup; here I just give
  // them a name
  setup(props, context) {
    // ref is for any type, reactive is for objects;
    console.log(props.message, context);

    // Here's how we emit
    context.emit('myMessage', 'hello');
    const userName = ref('dkmullen');
    const firstName = ref('');
    const lastName = ref('');
    const user = reactive({
      name: 'Dennis',
      age: 57,
    });

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
      (user.name = 'Dennis Mullen'),
        (user.age = 58),
        (userName.value = 'dkmullen777');
    }, 3000);

    function changeSomething() {
      this.user.age -= 1;
    }

    function setFirstName(event) {
      firstName.value = event.target.value;
    }

    // Lifecycle hooks now imported and called as functions; no created or
    // beforeCreated, as these are replaced by setup itself;
    onMounted(() => {
      console.log('mounted');
    });

    return {
      user,
      userName,
      changeSomething,
      setFirstName,
      lastName,
      fullName,
    };
  },
};
</script>

<style></style>
