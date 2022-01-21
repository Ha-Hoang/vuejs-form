<template>
  <form @submit.prevent="submitForm">
    <fImage />
    <div class="form-control">
      <label for="user-name">UserName</label>
      <input
        id="user-name"
        name="user-name"
        type="text"
        placeholder="Enter UserName"
        @input="validateUserName"
        @blur="validateUserName"
        v-model.trim="user.userName"
        :class="{ invalid: errors.userName }"
      />
      <fError :errors="errors.userName" />
    </div>
    <div class="form-control">
      <label for="password">Password</label>
      <input
        id="password"
        name="password"
        type="password"
        placeholder="Enter Password"
        @input="validatePassWord"
        @blur="validatePassWord"
        v-model="user.passWord"
        :class="{ invalid: errors.passWord }"
      />
      <fError :errors="errors.passWord" />
    </div>
    <f-button />
  </form>
</template>

<script>
import fImage from "./f-image.vue";
import fError from "./f-error.vue";
import fButton from "./f-button.vue";

export default {
  components: { fImage, fError, fButton },
  data() {
    return {
      errors: {
        userName: "",
        passWord: "",
      },
      user: {
        userName: "",
        passWord: "",
      },
    };
  },
  methods: {
    validateUserName() {
      let isValid = true;

      this.errors.userName = "";

      if (!this.user.userName) {
        this.errors.userName = "User Name is required!";
        isValid = false;
      }

      return isValid;
    },
    validatePassWord() {
      let isValid = true;

      this.errors.passWord = "";

      if (!this.user.passWord) {
        this.errors.passWord = "Password is required!";
        isValid = false;
      } else if (
        !this.isPassSpecialCharacter(this.user.passWord) ||
        !this.isPassIncludeNumber(this.user.passWord) ||
        this.user.passWord.length < 8
      ) {
        this.errors.passWord =
          "Password must have at least 8 character, 1 special character, number";
        isValid = false;
      }

      return isValid;
    },
    isPassSpecialCharacter(pass) {
      return /[ `!@#$%^&*()_+\-=[\]{};':"\\|,.<>/?~]/.test(pass);
    },
    isPassIncludeNumber(pass) {
      return /\d/.test(pass);
    },
    submitForm() {
      if (this.validatePassWord() && this.validateUserName()) {
        alert("login successfully!");
        this.user = "";
      } else {
        this.validateUserName();
        this.validatePassWord();
      }
    },
  },
};
</script>

<style>
form {
  background-color: #ffffff;
  max-width: 40rem;
  border: 0.5rem solid grey;
  margin: 5rem auto;
}

.form-img {
  max-width: 176px;
  margin: auto;
  margin-top: 1rem;
}

.form-img img {
  width: 10rem;
  height: 10rem;
}

.form-control {
  margin: 0.6rem 0.4rem;
}

.form-control p {
  color: red;
}

.form-control .invalid {
  border-color: red;
}

.form-control .feedback {
  color: red;
}

label {
  font-weight: bold;
}

input {
  display: block;
  width: 100%;
  padding: 0.4rem;
}

form div button {
  width: 100%;
  background-color: green;
  cursor: pointer;
  border: none;
  color: #fff;
  padding: 0.4rem;
  margin: 1rem 0rem;
}
</style>
