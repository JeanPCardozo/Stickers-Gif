<template>
  <div class="home">
    <br />
    <br />
    <div class="columns is-mobile is-centered">
      <div class="column is-3-mobile is-1-desktop is-1-tablet">
        <figure class="image is-128x128">
          <img alt="Vue logo" src="../assets/logo.png" />
        </figure>
      </div>
    </div>
    <div class="columns  is-mobile is-centered">
      <div class="column is-11 has-text-centered">
        <p>
          La app Stickers & Gifs está provista de muchos elementos, esta app
          está desarrollada en
          <a
            href="https://v3.vuejs.org/"
            target="_blank"
            rel="noopener noreferrer"
            ><i>Vue.js 3</i></a
          >
          y haciendo uso de la api
          <a
            href="https://developers.giphy.com/"
            target="_blank"
            rel="noopener noreferrer"
            ><i>giphy</i></a
          >.
        </p>
      </div>
    </div>
    <br />
    <br />
    <hr />
    <div class="has-text-centered">
      <p>Author, Jean Cardozo</p>
      <br />
      <a
        href="https://github.com/JeanPCardozo"
        class="button is-dark"
        target="_blank"
        rel="noopener noreferrer"
        >GitHub</a
      >
    </div>
  </div>
</template>

<script>
export default {
  name: "Home",
  components: {},
};
</script>
