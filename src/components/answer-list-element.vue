<template>
  <section v-if="answer">

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
    }
  }
</script>
