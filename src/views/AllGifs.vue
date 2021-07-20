<template>
  <div id="allGifs">
    <p class="is-size-2 has-text-centered">Gifs</p>
    <hr />
    <div class="control columns is-mobile is-multiline is-centered">
      <div class="column is-9-desktop is-6-tablet is-8-mobile">
        <input
          class="input"
          type="text"
          v-model="search"
          placeholder="Buscar Gif...."
        />
      </div>
      <div class="column is-2-desktop is-2-tablet is-2-mobile">
        <button
          class="button is-success"
          :class="load ? 'is-loading' : ''"
          @click="gifFiltered"
        >
          Buscar
        </button>
      </div>
    </div>

    <loading v-if="pageLoad" />

    <div v-else class="columns is-mobile is-multiline is-centered">
      <Gifs
        v-for="gif in gifs"
        :key="gif.id"
        :src="gif.images.downsized.url"
        :title="gif.title"
        :user="gif.user"
        class="column is-6-mobile is-3-tablet is-2-desktop"
      />
    </div>
  </div>
</template>

<script>
import Gifs from "../components/Gifs.vue";
import loading from "../components/loading.vue";
export default {
  data: () => ({
    gif: {},
    filterGif: {},
    search: "",
    load: false,
    pageLoad: false,
    apiKey: "eri0oGt9xiX5y78RKPhvoWfCQmyGQDUG",
  }),
  components: {
    Gifs,
    loading,
  },
  computed: {
    gifs() {
      return this.search != "" ? this.filterGif : this.gif;
    },
  },
  methods: {
    async getTrendingGifs() {
      this.pageLoad = true;
      const URL = "https://api.giphy.com/v1/gifs/trending";
      const { data } = await this.axios.get(`${URL}?api_key=${this.apiKey}`);
      this.gif = data.data;
      this.pageLoad = false;
    },
    async gifFiltered() {
      this.load = true;
      this.pageLoad = true;
      const URL = "https://api.giphy.com/v1/gifs/search";
      const { data } = await this.axios.get(
        `${URL}?api_key=${this.apiKey}&q=${this.search}`
      );
      let filtered = data.data;
      this.filterGif = filtered;
      this.load = false;
      this.pageLoad = false;
    },
  },
  mounted() {
    this.getTrendingGifs();
  },
};
</script>
