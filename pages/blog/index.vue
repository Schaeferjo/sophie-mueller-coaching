<template>
  <div>
    <h1>Blog</h1>
    <ul>
      <li v-for="post of posts" :key="post.slug">
        <NuxtLink :to="'/blog/' + post.slug">{{ post.title }}</NuxtLink>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  async asyncData({ $content }) {
    const posts = await $content('blog').fetch()

    return {
      posts,
    }
  },
}
</script>
