<template>
  <div class="auth-page">
    <div class="container page">
      <div class="row">
        <div class="col-md-6 offset-md-3 col-xs-12">
          <h1 class="text-xs-center">Sign in</h1>
          <!-- <p class="text-xs-center">
            <router-link :to="{ name: 'register' }">
              Need an account?
            </router-link>
          </p> -->
          <!-- <ul v-if="errors" class="error-messages">
            <li v-for="(v, k) in errors" :key="k">
              {{ k }} {{ errorFilter(v) }}
            </li>
          </ul> -->
          <form @submit.prevent="onSubmit(email, password)">
            <fieldset class="form-group">
              <input
                class="form-control form-control-lg"
                type="text"
                v-model="email"
                placeholder="Email"
              />
            </fieldset>
            <fieldset class="form-group">
              <input
                class="form-control form-control-lg"
                type="password"
                v-model="password"
                placeholder="Password"
              />
            </fieldset>
            <button class="btn btn-lg btn-primary pull-xs-right">
              Sign in
            </button>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { mapState } from "vuex";
import axios from "axios";
export default {
  name: "RwvLogin",
  data() {
    return {
      email: null,
      password: null,
    };
  },
  methods: {
    onSubmit(email, password) {
      axios
        .post(
          "https://api.realworld.io/api/users/login",
          { user: { email: email, password: password } },
          { headres: { Accept: "*/*" } }
        )
        .then(() => this.$router.push({ name: "about" }))
        .catch((error) => console.log(error));
    },
    errorFilter(errorValue) {
      return `${errorValue[0]}`;
    },
  },
  computed: {
    ...mapState({
      errors: (state) => state.auth.errors,
    }),
  },
};
</script>
