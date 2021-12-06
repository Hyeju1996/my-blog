<template>
  <div>
    <Header />
    <h1>Hello world</h1>
    <nuxt-content :document="doc" />
  </div>
</template>


<script>
export default {
  async asyncData({ $content, params }) {
    const doc = await $content("history", params.slug).fetch();

    return { doc };
  },
};
</script>

<style scoped>
.nuxt-content-container {
  background-color: gray;
  border: 1px solid black;
}
</style>