<template>
  <div class="home col-8 mx-auto py-5 mt-5">
    <h1>Dashboard</h1>
    <div class="card">
      <div class="card-body" v-if="user">
        <h3>Hello, {{ user.name }}</h3>
        <span>{{ user.email }}</span><br>
        <span>{{ birthDate }}</span>
      </div>
    </div>
  </div>
</template>

<script>
import User from "../apis/User";

export default {
  data() {
    return {
      user: null,
      birthDate: null
    };
  },

  mounted() {
    User.auth().then(response => {
      this.user = response.data;
    });

    User.birthdate().then(response => {
      this.birthDate = response.data;
    });

  }
};
</script>
