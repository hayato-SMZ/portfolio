<template>
  <div>
    <div v-for="b in blogs" :key="b.slug">
      <nuxt-link :to="'/blogs/' + b.slug">{{ b.title }} {{ b.date }}</nuxt-link>
    </div>
  </div>
</template>
<script>
export default {
  async asyncData({ $content, params }) {
    const limit = 10;
    const query = await $content('blogs' || 'index').limit(limit)
    const blogs = await query.fetch()
    console.log(blogs);
    return { blogs }
  },
}
</script>
