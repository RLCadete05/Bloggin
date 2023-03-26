<template>
  <v-app dark>
    <Header />
    <v-main>
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>
    <Footer />
  </v-app>
</template>

<script>
import Header from "../components/Header.vue";
import Footer from "../components/Footer.vue"

export default {
  name: "Default",
  components: {
    Header,
    Footer,
  },
};
</script>

<style>
html, body{
    font-family: "Nunito", sans-serif;
}
::-webkit-scrollbar {
  width: 10px;
}

::-webkit-scrollbar-thumb {
  background: #0D47A1; 
  border-radius: 10px;
}
</style>
