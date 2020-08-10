<template>
  <div>
    <h4 class="text-light mb-3">Search Results</h4>

    <div class="d-flex flex-wrap justify-space-around">
      <img
        v-for="gif in resultGifs"
        :key="gif.id"
        :src="gif.images.fixed_height.url"
        :alt="gif.title"
        class="my-3"
      />
    </div>

    <div class="text-center my-4">
      <v-btn
        :loading="loading"
        :disabled="loading"
        depressed
        color="#6930c3"
        dark
        x-large
        @click="loadMore"
      >Load more</v-btn>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "SearchResults",

  data: () => ({
    resultGifs: [],
    loading: false,
  }),

  props: ["query"],

  created: function () {
    this.loading = true;
    axios
      .get("https://api.giphy.com/v1/gifs/search", {
        params: { api_key: "n3Gbo6ADDbBVDNmyjP87XiGXAoLcGf3s", q: this.query },
      })
      .then((response) => {
        this.resultGifs = response.data.data;
        this.loading = false;
      });
  },

  watch: {
    query: function (query) {
      this.loading = true;
      axios
        .get("https://api.giphy.com/v1/gifs/search", {
          params: { api_key: "n3Gbo6ADDbBVDNmyjP87XiGXAoLcGf3s", q: query },
        })
        .then((response) => {
          this.resultGifs = response.data.data;
          this.loading = false;
        });
    },
  },

  methods: {
    loadMore() {
      this.loading = true;
      axios
        .get("https://api.giphy.com/v1/gifs/search", {
          params: {
            api_key: "n3Gbo6ADDbBVDNmyjP87XiGXAoLcGf3s",
            q: this.query,
            limit: "5",
            offset: this.resultGifs.length,
          },
        })
        .then((response) => {
          this.resultGifs.push(...response.data.data);
          this.loading = false;
        });
    },
  },
};
</script>
