<template>
  <div>
    <nav class="navbar is-dark">
      <div class="navbar-brand">
        <router-link class="navbar-item" to="/">
          <img
            src="../assets/logo.png"
            alt="Bulma: a modern CSS framework based on Flexbox"
            width="30"
            height="30"
          />
          <p class="is-size-6">GIFS & STICKERS</p>
        </router-link>
        <div
          class="navbar-burger"
          :class="isActive ? 'is-active' : ''"
          @click="clickButtom"
          data-target="navbarExampleTransparentExample"
        >
          <span></span>
          <span></span>
          <span></span>
        </div>
      </div>

      <div
        id="navbarExampleTransparentExample"
        class="navbar-menu"
        :class="isActive ? 'is-active' : ''"
      >
        <div class="navbar-start">
          <router-link class="navbar-item" to="/">Home</router-link>
          <router-link class="navbar-item" to="/Stickers">Stickers</router-link>
          <router-link class="navbar-item" to="/Gifs">Gifs</router-link>
        </div>
      </div>
    </nav>
  </div>
</template>

<script>
export default {
  data: () => ({
    isActive: false,
  }),
  methods: {
    clickButtom() {
      this.isActive = !this.isActive;
    },
  },
};
</script>

<style></style>
