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
export default {
  name: 'IndexPage',
  data () {
    return {
      articles: [
        {
          id: 'mi-primer-post',
          title: 'Mi primer post',
          description: 'Post realizado para el miniblog',
          author: 'Ameth Ordoñez',
          date: new Date('2022-10-24'),
          cover: 'https://picsum.photos/300/200'
        }
      ]
    }
  },
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
