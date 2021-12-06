<template>
  <div>
    <Header />
    <ul>
      <li v-for="doc in docs" :key="doc.slug">
        <nuxtLink :to="doc.path">
          <span>{{ doc.title }}</span> <br /> </nuxtLink
        >> <span>{{ doc.description }}</span> <br />
        <span>{{ doc.createdAt }}</span> <br />
        <img :src="doc.image - upload" :alt="doc.slug" />
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  head() {
    return {
      script: [
        { src: "https://identity.netlify.com/v1/netlify-identity-widget.js" },
      ],
    };
  },

  async asyncData({ $content, params }) {
    const docs = await $content("history").fetch();
    console.log(docs);
    return { docs };
  },
};
</script>

<style scoped>
</style>