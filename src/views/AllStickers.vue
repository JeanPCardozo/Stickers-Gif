<template>
  <div id="allGifs">
    <p class="is-size-2 ">Stickers</p>
    <hr />
    <div class="field">
      <div class="control columns is-mobile is-multiline is-centered">
        <div class="column is-9-desktop is-6-tablet is-8-mobile">
          <input class="input" type="text" placeholder="Buscar Gif...." />
        </div>
        <div class="column is-2-desktop is-2-tablet is-2-mobile">
          <button class="button is-success">Buscar</button>
        </div>
      </div>
    </div>
    <div class="columns is-mobile is-multiline is-centered">
      <Stickers class="column is-6-mobile is-3-tablet is-2-desktop" />
    </div>
  </div>
</template>

<script>
import Stickers from "../components/Stickers.vue";
export default {
  data: () => ({}),
  components: {
    Stickers,
  },
};
</script>
