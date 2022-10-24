<template>
  <div class="about-me">
    <h1>Miniblog</h1>
    <p>
      Miniblog es un pequeño sistema de blog personal con NuxtJS, Netlify y
      Airtable.
    </p>
  </div>
</template>

<style lang="scss" scoped>
.about-me {
  @apply w-full flex flex-col justify-center items-center px-4 py-16 text-white bg-gradient-to-r from-indigo-500 via-purple-500 to-pink-500;
  h1 {
    @apply font-black text-4xl text-white pb-2;
  }
  p {
    @apply text-lg py-2;
  }
}
</style>
