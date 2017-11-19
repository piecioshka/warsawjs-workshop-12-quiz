<template>
  <section v-if="answers" class="panel">
    <!--<h1 class="subtitle">-->
    <!--Liczba odpowiedzi: {{ answers.length }}-->
    <!--</h1>-->

    <answer-list-element
      v-for="(answer, index) in answers"
      :key="answer"
      :answer="answer"
      :answerIndex="index"
      :question="question"
      class="panel-block"
      @selectAnswer="onSelectAnswer(index)"
    ></answer-list-element>

  </section>
</template>

<script>
  import AnswerListElement from './answer-list-element.vue';

  export default {
    components: { AnswerListElement },
    name: 'AnswerList',
    props: {
      answers: Array,
      question: Object
    },
    methods: {
      onSelectAnswer(selectAnswerIndex) {
        this.$emit('selectAnswerIndex', selectAnswerIndex);
      }
    }
  }
</script>
