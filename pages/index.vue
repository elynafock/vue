<template>
  <section class="container">
    <div>
      <logo />
      <h1 class="title">nuxt-fundamentals</h1>
      <h2 class="subtitle">My gnarly Nuxt.js project</h2>
      <div class="links">
        <nuxt-link
          v-for="post in posts"
          :to="{ name: 'post-id', params: { id: 'balut' } }"
          :key="post.id"
          class="button--grey"
        >
        {{post.title}}
        </nuxt-link>
      </div>
    </div>
  </section>
</template>

<script>
import Logo from "~/components/NuxtLogo.vue";

export default {
  components: {
    Logo,
  },
  data() {
    return {
      posts: this.$store.state.posts.all
    }
  },
  head() {
    return{
head(){
    return {
      title: this.posts.title,
      meta: [
        { name: 'twitter:title', content: this.posts.title},
        { name: 'twitter:description', content: this.posts.content},
        { name: 'twitter:image', content:'/meow.jpeg'},
      ]
    }
  },    }
  }
};
</script>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  letter-spacing: 1px;
}
.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
}
.links {
  padding-top: 15px;
}
</style>
