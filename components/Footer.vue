<template>
    <div>
    <v-footer padless>
      <v-col
        class="text-center"
        cols="12"
      ><span>
        &copy; CopyRight, <strong>Bloggin</strong> - {{ new Date().getFullYear() }}
      </span>
        
      </v-col>
    </v-footer>
  </div>
</template>

<script>
export default{
    name: "Footer",
}
</script>
