<template>
  <v-col class="d-flex child-flex" cols="12" sm="4" md="4">
    <v-hover v-slot="{ hover }">
      <v-card
        class="mb-10"
        id="card"
        style="cursor: pointer; border-radius: 10px"
        tile
        width="316"
        :elevation="hover ? 12 : 2"
        :class="{ 'on-hover': hover }"
        @click="toCards()"
      >
        <v-img
          class="mx-auto"
          height="181"
          lazy-src="https://picsum.photos/500/300?image=50"
          src="https://picsum.photos/1080/920?image=50"
        ></v-img>
        <v-card-title>{{ card.title }}</v-card-title>
      </v-card>
    </v-hover>
  </v-col>
</template>

<script>
export default {
  name: "FlagsCard",
  props: {
    card: Object,
  },
  methods: {
    toCards() {
      this.$router.push({ path: `/idCards/${this.card.id}` });
    },
  },
};
</script>

<style>
#card {
  transition: opacity 0.4s ease-in-out;
}

#card:not(.on-hover) {
  opacity: 0.6;
}

.show-btns {
  color: rgba(255, 255, 255, 1) !important;
}
</style>
