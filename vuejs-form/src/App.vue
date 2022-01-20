<template>
  <section>
    <fLogin />
  </section>
</template>

<script>
import fLogin from "./components/f-login.vue";

export default {
  components: {
    fLogin,
  },
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
  background-color: #292929;
}
</style>
