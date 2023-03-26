<template>
  <div>
    <v-btn
      elevation="2"
      width="136"
      class="font-weight-regular text-capitalize hidden-sm-and-down"
      outlined
      tile
      color="#0D47A1"
      @click="toUsers"
    >
      <v-icon dense style="margin-rigth:5px"> mdi-account-circle </v-icon>
      Usuários
    </v-btn>
    <v-btn
      elevation="0"
      width="40"
      class="font-weight-regular text-capitalize hidden-sm-and-up"
      @click="toUsers"
    >
      <v-icon dense style="margin-rigth:5px"> mdi-account-circle </v-icon>
    </v-btn>
  </div>
</template>

<script>
export default {
  name: 'Users',
  methods: {
    toUsers() {
      this.$router.push({ path: '/users' })
    }
  }
}
</script>
