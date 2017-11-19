<template>
  <section v-if="question" class="message">
    <div class="message-header">
      <h4>{{ question.title }}</h4>
    </div>

    <div class="message-body">
      <answer-list
        :answers="question.answers"
      ></answer-list>
    </div>
  </section>
</template>

<script>
  import AnswerList from './answer-list.vue';

  export default {
    name: 'QuestionListElement',
    components: { AnswerList },
    props: {
      question: Object
    }
  }
</script>
