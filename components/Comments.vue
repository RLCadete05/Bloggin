<template>
    <div>
      <v-list>
        <v-list-item class="d-flex">
          <v-avatar  class="mt-3 mr-3 align-self-start" color="#cecece" size="40">
            <v-icon x-large> mdi-account-circle </v-icon>
          </v-avatar>

          <v-list-item-content class="blue-grey lighten-5" style="padding: 10px; border-radius:10px">
              <div>
                <span class="ml-2 font-weight-medium font-italic">{{ comment.name }} -</span>
                <a class="font-italic" href="mailto:">{{ comment.email }}</a>
              </div>
              <div>
                {{ comment.body }}
              </div>
          </v-list-item-content>

        </v-list-item>
      </v-list>
    </div>
</template>

<script>
export default{
    name: "Comments",

    props: {
        comment: Object,
    }
}
</script>

