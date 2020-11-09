<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <h1>Blog</h1>
      <ul>
        <li v-for="post of posts" :key="post.slug">
          <NuxtLink :to="'/blog/' + post.slug">{{ post.title }}</NuxtLink>
        </li>
      </ul>
    </v-col>
  </v-row>
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
