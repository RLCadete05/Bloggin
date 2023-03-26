<template>
  <div>
    <v-app-bar fixed app height="80">
      <div>
        <NuxtLink to="/"
          ><img
            src="../assets/Bloggin.png"
            alt="Logo Bloggin"
            height="180px"
            class="mr-4"
        /></NuxtLink>
      </div>
      <v-spacer />
      <Posts style="margin-right: 10px" />
      <Users />
    </v-app-bar>
  </div>
</template>

<script>
import Users from "./buttons/Users.vue";
import Posts from "./buttons/Posts.vue";

export default {
  name: "Header",
  components: {
    Users,
    Posts,
  },
};
</script>
