<template>
  <v-app id="app">
    <v-container class="app-container">
      <v-row>
        <v-col>
          <Navbar />
        </v-col>
      </v-row>

      <v-row>
        <v-col>
          <Searchbar @userHasSearched="userHasSearched($event)" />
        </v-col>
      </v-row>

      <v-row>
        <v-col>
          <Trending v-if="!userSearch" />
          <SearchResults v-else :query="searchQuery" />
        </v-col>
      </v-row>
    </v-container>
  </v-app>
</template>

<script>
import Navbar from './components/Navbar';
import Searchbar from './components/Searchbar';
import Trending from './components/Trending';
import SearchResults from './components/SearchResults';

export default {
  name: 'App',

  components: {
    Navbar,
    Searchbar,
    Trending,
    SearchResults,
  },

  data: () => ({
    userSearch: false,
    searchQuery: '',
  }),

  methods: {
    userHasSearched($event) {
      this.userSearch = false;
      this.searchQuery = $event;
      this.userSearch = true;
    },
  },
};
</script>

<style>
#app {
  min-height: 100vh;
  background-color: rgb(18, 18, 18);
  padding: 2rem;
  color: #fff;
}
.app-container {
  max-width: 1040px !important;
}
</style>
