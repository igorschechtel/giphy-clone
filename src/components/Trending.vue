<template>
  <div>
    <h4 class="text-light mb-3">Trending GIFs</h4>

    <div class="d-flex flex-wrap justify-space-around">
      <img
        v-for="gif in trendingGifs"
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
      >
        Load more
      </v-btn>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'Trending',

  data: () => ({
    trendingGifs: [],
    loading: false,
  }),

  beforeCreate: function() {
    axios
      .get('https://api.giphy.com/v1/gifs/trending', {
        params: { api_key: 'n3Gbo6ADDbBVDNmyjP87XiGXAoLcGf3s', limit: '10' },
      })
      .then((response) => {
        this.trendingGifs = response.data.data;
      });
  },

  methods: {
    loadMore() {
      this.loading = true;
      axios
        .get('https://api.giphy.com/v1/gifs/trending', {
          params: {
            api_key: 'n3Gbo6ADDbBVDNmyjP87XiGXAoLcGf3s',
            limit: '5',
            offset: this.trendingGifs.length,
          },
        })
        .then((response) => {
          this.trendingGifs.push(...response.data.data);
          this.loading = false;
        });
    },
  },
};
</script>
