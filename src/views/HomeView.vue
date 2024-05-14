<template>
  <div class="home">
    <LoginUser msg="Welcome to Your Vue.js + TypeScript App" />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import LoginUser from "@/components/LoginUser.vue"; // @ is an alias to /src

export default defineComponent({
  name: "HomeView",
  components: {
    LoginUser,
  },
});
</script>
