<template>
  <div class="feedback" v-if="errors">{{ errors }}</div>
</template>

<script>
export default {
  props: ["errors"],
};
</script>
