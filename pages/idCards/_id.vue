<template>
  <div>
    <div class="mt-2 mx-auto" style="width: 70%">
      <h1 class="text-center">Comentários</h1>
      <v-divider />
      <br />
      <br />
      <h1 class="text-left">{{ idCards.title }}</h1>
      <br />
      <v-img
        class="mx-auto"
        height="181"
        lazy-src="https://picsum.photos/1080/920?image=50"
        src="https://picsum.photos/1080/920?image=50"
        style="border-radius: 10px"
      ></v-img>
      <div class="container-cards">
        <p>{{ idCards.body }}</p>

        <h3 class="my-6">
          <v-icon>mdi mdi-comment </v-icon
          > {{ comments.length }} Comentários
        </h3>

        <Comments
          v-for="comment in comments"
          :key="comment.id"
          :comment="comment"
        />
      </div>
    </div>
  </div>
</template>

<script>
import Comments from "../../components/Comments.vue";

export default {
  data() {
    return {
      id: this.$route.params.id,
      pagination: {
        page: 1,
        total: 0,
        perPage: 12,
        visible: 7,
      },
      idCards: {},
      comments: [],
    };
  },

  components: {
    Comments,
  },

  async created() {
    await this.getCards();
  },
  methods: {
    async getCards() {
      try {
        const response = await this.$axios.$get(`/posts/${this.id}`);
        const responseComments = await this.$axios.$get(
          `/posts/${this.id}/comments`
        );

        this.idCards = response;
        this.comments = responseComments;
      } catch (error) {
        throw new Error(error);
      }
    },
  },
};
</script>

<style scoped>
.container-cards {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  max-width: 100%;
  margin-top: 20px;
}

.container-pagination {
  width: 100%;
  display: flex;
  justify-content: center;
}

.pagination {
  position: fixed;
  bottom: 0;
  margin-bottom: 20px;
}
</style>
