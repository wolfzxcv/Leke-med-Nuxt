<template>
  <nuxt-link :to="`jokes/${id}`">
    <div class="joke">
      <p>{{ joke }}</p>
    </div>
  </nuxt-link>
</template>

<script>
export default {
  props: {
    joke: String,
    id: String
  }
};
</script>

<style>
.joke {
  padding: 1rem;
  border: 1px #ccc dotted;
  margin: 1rem 0;
}
</style>
