<script setup lang="ts">
import { onMounted } from "vue";
import pocketbase  from "pocketbase";

let pb = null;
onMounted(async() => {
  pb = new pocketbase("http://127.0.0.1:8090");

 const authData = await pb.collection('users').authWithPassword('dre10155', 'password');
  // after the above you can also access the auth data from the authStore
console.log('Is user authenticated:',pb.authStore.isValid);
console.log('User Token:',pb.authStore.token);
console.log(pb.authStore.model?.id);

// "logout" the last authenticated model
pb.authStore.clear();
});
</script>

<template>
  <div>
    <h1>Hello World</h1>
  </div>
  <HelloWorld msg="Vite + Vue" />
</template>

<style scoped></style>
