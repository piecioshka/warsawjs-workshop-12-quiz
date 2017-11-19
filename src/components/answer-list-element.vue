<template>
  <section v-if="answer" @click="onClick()">

    <p>
      {{ answer }}
    </p>

  </section>
</template>

<script>
  export default {
    name: 'AnswerListElement',
    props: {
      answer: String
    },
    methods: {
      onClick() {
        this.$emit('selectAnswer', this.answer)
      }
    }
  }
</script>

<style scoped>
  section {
    display: block;
  }

  section:hover {
    background: lightseagreen;
    color: white;
    cursor: pointer;
  }
</style>
