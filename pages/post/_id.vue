<template>
  <div class="container">
    <article>
      <h1 class="title">{{foundPost.title}}</h1>
      <p>
       {{foundPost.contents}}
      </p>
    </article>
    <aside>
      Post you may enjoy 
      <ul>
        <li v-for="related in relatedPost">
         <nuxt-link :to="`/post/${related.id }`">{{related.title}}</nuxt-link></li>
      </ul>
    </aside>
  </div>
</template>

<script>
export default {
  head(){
    return {
      title: this.foundPost.title,
      meta: [
        { name: 'twitter:title', content: this.foundPost.title},
        { name: 'twitter:description', content: this.foundPost.content},
        { name: 'twitter:image', content:'~/assets/meow.jpeg'}
      ]
    }
  },
  data() {
    return {
      id: this.$route.params.id,
    };
  },
  computed: {
    foundPost() {
      return this.$store.state.posts.all.find(post => post.id === this.id)
    },
  relatedPost() {
    return this.$store.state.posts.all.filter(post => post.id !== this.id)
  }


  }
};
</script>

<style scoped>
.container {
  display: flex;
  justify-content: space-between;
  line-height: 1.5;
}
article * {
  margin-bottom: 1rem;
}
aside {
  min-width: 280px;
  max-width: 280px;
  padding-left: 2rem;
}
.title {
  font-size: 2rem;
}
</style>
