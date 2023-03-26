<template>
  <div>
    <div class="container-cards">
      <FlagsCard v-for="card in paginatedItems" :key="card.id" :card="card" />
    </div>

    <div class="container-pagination">
      <v-pagination
        class="pagination"
        color="#0D47A1"
        v-model="pagination.page"
        :length="pagination.total"
        :total-visible="pagination.visible"
      ></v-pagination>
    </div>
  </div>
</template>

<script>
import FlagsCard from "../components/Flags/FlagsCards.vue";

export default {
  name: "IndexPage",
  data() {
    return {
      cards: [],
      pagination: {
        page: 1,
        total: 0,
        perPage: 9,
        visible: 7,
      },
    };
  },
  components: {
    FlagsCard,
  },
  async mounted() {
    await this.getAll();
  },
  methods: {
    async getAll() {
      try {
        const response = await this.$axios.$get("/posts");

        this.cards = response;
        this.pagination.total = Math.ceil(
          this.cards.length / this.pagination.perPage
        );
      } catch (error) {
        throw new Error(error);
      }
    },
  },
  computed: {
    paginatedItems() {
      let page = this.pagination.page - 1;
      const perPage = this.pagination.perPage;
      let start = page * perPage;
      let end = start + perPage;

      const paginatedItems = this.cards;

      return paginatedItems.slice(start, end);
    },
  },
};
</script>

<style>
body {
  font-family: "Nunito", sans-serif;
}
.container-cards {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  max-width: 100%;
  margin-top: 20px;
}

.container-pagination {
  min-width: 100%;
  display: flex;
  justify-content: center;
}

.pagination {
  position: fixed;
  bottom: 0;
  margin-bottom: 20px;
}
</style>
