<template>
  <div style="margin-bottom:20px">
    <div class="card">
      <div class="card-image">
        <figure class="image is-4by3">
          <img :src="src" alt="Placeholder image" />
        </figure>
      </div>
      <div class="card-content">
        <div v-if="user != {}" class="media">
          <div class="media-left">
            <figure class="image is-48x48">
              <img :src="user.avatar_url" alt="avatar user" />
            </figure>
          </div>
          <div class="media-content">
            <p class="title is-4">{{ user.username }}</p>
            <p class="subtitle is-6">
              <a
                :href="user.website_url"
                target="_blank"
                rel="noopener noreferrer"
                >{{ user.website_url }}</a
              >
            </p>
          </div>
        </div>

        <div class="content">
          <p class="is-size-4">{{ title }}</p>
          <p v-if="user != {}">{{ user.description }}</p>
        </div>
      </div>
      <footer class="card-footer">
        <button href="#" class="button is-info card-footer-item">
          Descargar
        </button>
      </footer>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    src: String,
    title: String,
    user: {
      type: Object,
      default: {},
    },
  },
};
</script>

<style></style>
