<template>
  <div>
    <v-btn
      elevation="2"
      width="136"
      class="mr-6 font-weight-regular text-capitalize hidden-sm-and-down"
      outlined
      tile
      color="#0D47A1"
      @click="toPosts"
    >
      <v-icon dense style="margin-rigth:5px"> mdi mdi-post </v-icon>
      Postagens
    </v-btn>
    <v-btn
      elevation="0"
      width="30"
      class="font-weight-regular text-capitalize hidden-sm-and-up"
      @click="toPosts"
    >
      <v-icon dense style="margin-rigth:5px"> mdi mdi-post </v-icon>
    </v-btn>
  </div>
</template>

<script>
export default {
  name: 'Posts',
  methods: {
    toPosts() {
      this.$router.push({ path: '/' })
    }
  }
}
</script>
