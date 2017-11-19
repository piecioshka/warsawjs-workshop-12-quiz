<template>
  <section v-if="answers" class="panel">
    <!--<h1 class="subtitle">-->
    <!--Liczba odpowiedzi: {{ answers.length }}-->
    <!--</h1>-->

    <answer-list-element
      v-for="answer in answers"
      :key="answer"
      :answer="answer"
      class="panel-block"
    ></answer-list-element>

  </section>
</template>

<script>
  import AnswerListElement from './answer-list-element.vue';

  export default {
    components: { AnswerListElement },
    name: 'AnswerList',
    props: {
      answers: Array
    }
  }
</script>
