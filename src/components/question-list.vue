<template>
  <section v-if="questions">
    <!--<h1 class="title">-->
    <!--Liczba pytań: {{ questions.length }}-->
    <!--</h1>-->

    <question-list-element
      v-for="question in questions"
      :key="question.title"
      :question="question"
    ></question-list-element>
  </section>
</template>

<script>
  import QuestionListElement from './question-list-element.vue';

  export default {
    components: { QuestionListElement },
    name: 'QuestionList',
    props: {
      questions: Array
    }
  }
</script>
