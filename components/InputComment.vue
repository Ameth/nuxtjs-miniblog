<template>
  <form class="input-comment" @submit.prevent="submit">
    <legend>Comentar</legend>
    <label for="name">Nombre</label>
    <input v-model="name" name="name" type="text" />
    <label for="email">Correo</label>
    <input v-model="email" name="email" type="email" />
    <label for="content">Comentario</label>
    <textarea
      v-model="content"
      name="content"
      cols="30"
      rows="4"
      placeholder="Escribe aquí tu comentario"
    >
    </textarea>
    <button>Comentar</button>
    <div class="alert" :class="{ hidden: isHidden }">
      ¡Comentario enviado correctamente!
    </div>
  </form>
</template>

<script>
export default {
  name: 'InputComment',
  data () {
    return {
      name: '',
      email: '',
      content: '',
      isHidden: true
    }
  },
  methods: {
    submit (e) {
      this.$emit('submit', {
        name: this.name,
        email: this.email,
        content: this.content.slice(0, 120)
      })
      this.name = ''
      this.email = ''
      this.content = ''
      this.isHidden = false
      setTimeout(() => {
        this.isHidden = true
      }, 3000)
    }
    // showAlert(){
    //     this.$emit('update:hidden', true)
    // }
  }
}
</script>

<style lang="scss" scoped>
.input-comment {
  @apply flex flex-col gap-2 mt-6 mb-4;
  legend {
    @apply text-xl font-bold;
  }
  label {
    @apply text-gray-600;
  }
  input,
  textarea {
    @apply p-2;
  }
  button {
    @apply border bg-gray-300 hover:bg-gray-400 px-4 py-2 text-center font-bold;
  }
}
.alert {
  @apply bg-lime-600 rounded-lg text-white p-2.5 text-center;
  .hidden {
    @apply invisible;
  }
}
</style>
