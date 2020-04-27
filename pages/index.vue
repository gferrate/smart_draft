<template>
  <b-container class="border rounded p-3 login mt-5 shadow-sm">
    <login />
  </b-container>
</template>

<script>
import Login from "~/components/Login.vue";

export default {
  components: {
    Login
  }
};
</script>

<style>
.login{
  max-width: 30rem;
}
</style>
