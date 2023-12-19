<template>
  <div class="d-flex justify-content-center align-items-center vh-100">
  
    <form @submit.prevent="submitForm">
      <div class="mb-3">
        <h2>Hallo Selamat Datang!!!</h2>
        <label for="exampleInputEmail1" class="form-label">Email</label>
        <input
          type="email"
          class="form-control"
          id="exampleInputEmail1"
          v-model="formData.email"
          aria-describedby="emailHelp"
        />
        <div id="emailHelp" class="form-text">
          Isi dengan benar!!.
        </div>
      </div>
      <div class="mb-3">
        <label for="exampleInputPassword1" class="form-label">Kata Sandi</label>
        <input
          type="password"
          class="form-control"
          id="exampleInputPassword1"
          v-model="formData.password"
        />
      </div>
      <button type="submit" class="btn btn-danger">Masuk</button>
    </form>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      formData: {
        email: "",
        password: "",
      },
    };
  },
  methods: {
    async submitForm() {
      try {
        // Make a POST request to the login endpoint without checking the response
        await axios.post(
          "http://localhost:3000/api/Users/login",
          this.formData
        );

        // Navigate to the home page on successful login
        this.$router.push("/home");
      } catch (error) {
        // Handle any errors here
        console.error("Error during login:", error.message);
        console.log("server respon : ", error.response);
      }
    },
  },
};
</script>

<style scoped>
.login-form {
  width: 400px;
  padding: 80px;
  border-radius: 40px;
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.1);
  margin-left: auto !important;
}
</style>
