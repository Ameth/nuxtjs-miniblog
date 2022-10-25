<template>
  <div class="container">
    <About />
    <div class="content">
      <main>
        <ArticleCard
          v-for="article in articles"
          :key="article.id"
          v-bind="article"
        />
      </main>
    </div>
  </div>
</template>

<script>
import About from '~/components/About.vue'
import ArticleCard from '../components/ArticleCard.vue'
import _idVue from './_id.vue'
export default {
  name: 'IndexPage',
  // data () {
  //   return {
  //     articles: []
  //   }
  // },
  async asyncData ({ isDev, $http }) {
    const baseUrl =
      isDev === true
        ? 'http://localhost:9999'
        : 'https://miniblog-nuxt-ameth.netlify.app'
    const url = `${baseUrl}/.netlify/functions/articles`
    const { articles } = await $http.$get(url)
    return {
      posts: articles
    }
  },
  computed: {
    articles () {
      return Array.isArray(this.posts)
        ? this.posts.map(item => {
            return {
              ...item,
              author: item['author-name'][0],
              date: new Date(item.updated),
              cover: 'https://picsum.photos/300/200'
            }
          })
        : []
    }
  },
  // async mounted () {
  //   const baseUrl =
  //     location.hostname === 'localhost'
  //       ? 'http://localhost:9999'
  //       : 'https://miniblog-nuxt-ameth.netlify.app'
  //   const url = `${baseUrl}/.netlify/functions/articles`
  //   const { articles } = await this.$http.$get(url)
  //   this.articles = articles.map(item => {
  //     return {
  //       ...item,
  //       author: item['author-name'][0],
  //       date: new Date(item.updated),
  //       cover: 'https://picsum.photos/300/200'
  //     }
  //   })
  // },
  components: { About, ArticleCard }
}
</script>

<style lang="scss">
.container {
  @apply m-auto;
}

.container .content {
  @apply flex flex-col justify-center items-center sm:p-2 md:p-4 lg:p-8 xl:p-16;

  main {
    @apply max-w-5xl grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6;
  }
}
</style>
