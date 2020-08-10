<template>
  <div>
    <form class="search-form" @submit="search">
      <v-row no-gutters>
        <v-col class="p-0">
          <input
            name="search_query"
            v-model="search_query"
            type="text"
            placeholder="Search all the GIFs"
          />
        </v-col>
        <v-col cols="auto">
          <button type="submit">
            <v-icon color="#fff" size="30px">search</v-icon>
          </button>
        </v-col>
      </v-row>
    </form>
  </div>
</template>

<script>
export default {
  name: 'Searchbar',

  data: () => ({
    search_query: '',
  }),

  methods: {
    search($event) {
      $event.preventDefault();
      this.$emit('userHasSearched', this.search_query);
    },
  },
};
</script>

<style scoped>
.search-form input {
  background-color: #fff;
  padding: 15px;
  height: 50px;
  width: 100%;
}
.search-form button {
  background-color: pink;
  height: 50px;
  padding: 0.4rem 0.8rem;
  background-image: linear-gradient(
    45deg,
    rgb(153, 51, 255) 0%,
    rgb(255, 102, 102) 50%,
    rgb(153, 51, 255) 100%
  );
  background-size: 400%;
  animation: 2s linear 0s infinite normal;
  background-position: 0% 100%;
}
</style>
