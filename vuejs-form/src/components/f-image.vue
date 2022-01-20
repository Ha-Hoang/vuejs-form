<template>
  <div class="form-img">
    <img :src="image" alt="img" />
  </div>
</template>

<script>
import image from "../assets/user.png";
export default {
  name: "fImage",
  data() {
    return {
      image: image,
    };
  },
};
</script>

