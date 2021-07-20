<template>
  <div id="allGifs">
    <p class="is-size-2 has-text-centered">Stickers</p>
    <hr />
    <div class="field">
      <div class="control columns is-mobile is-multiline is-centered">
        <div class="column is-9-desktop is-6-tablet is-8-mobile">
          <input
            class="input"
            type="text"
            v-model="search"
            placeholder="Buscar Sticker...."
          />
        </div>
        <div class="column is-2-desktop is-2-tablet is-2-mobile">
          <button
            class="button is-success"
            :class="load ? 'is-loading' : ''"
            @click="stickerFiltered"
          >
            <span style="margin-right:5px"><i class="fas fa-search"></i></span>
            Buscar
          </button>
        </div>
      </div>
    </div>
    <loading v-if="pageLoad" />
    <div v-else class="columns is-mobile is-multiline is-centered">
      <Stickers
        v-for="sticker in stickers"
        :key="sticker.id"
        :src="sticker.images.downsized.url"
        :title="sticker.title"
        :user="sticker.user"
        class="column is-6-mobile is-3-tablet is-2-desktop"
      />
    </div>
  </div>
</template>

<script>
import Stickers from "../components/Stickers.vue";
import loading from "../components/loading.vue";
export default {
  data: () => ({
    sticker: {},
    filterSticker: {},
    search: "",
    load: false,
    pageLoad: false,
    apiKey: "eri0oGt9xiX5y78RKPhvoWfCQmyGQDUG",
  }),
  components: {
    Stickers,
    loading,
  },
  computed: {
    stickers() {
      return this.search != "" ? this.filterSticker : this.sticker;
    },
  },
  methods: {
    async getTrendingStickers() {
      this.pageLoad = true;
      const URL = "https://api.giphy.com/v1/stickers/trending";
      const { data } = await this.axios.get(`${URL}?api_key=${this.apiKey}`);
      this.sticker = data.data;
      this.pageLoad = false;
    },
    async stickerFiltered() {
      this.load = true;
      this.pageLoad = true;
      const URL = "https://api.giphy.com/v1/stickers/search";
      const { data } = await this.axios.get(
        `${URL}?api_key=${this.apiKey}&q=${this.search}`
      );
      let filtered = data.data;
      this.filterSticker = filtered;
      console.log(this.filterSticker);
      this.load = false;
      this.pageLoad = false;
    },
  },
  mounted() {
    this.getTrendingStickers();
  },
};
</script>
