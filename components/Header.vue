<template>
  <div>
    <v-app-bar fixed app height="80">
      <div>
        <NuxtLink to="/"
          ><img
            src="../assets/Bloggin.png"
            alt="Logo Bloggin"
            height="120px"
        /></NuxtLink>
      </div>
      <v-spacer />
      <Posts />
      <Users />
    </v-app-bar>
  </div>
</template>

<script>

import Users from "./Buttons/Users.vue";
import Posts from "./Buttons/Posts.vue";

export default {
  name: "Header",
  components: {
    Users,
    Posts,
  },
};
</script>
