<template>
  <section v-if="quiz">
    <section class="hero is-primary">
      <div class="hero-body">
        <div class="container">
          <section class="columns">
            <section class="column is-three-quarters">
              <h1 class="title">
                {{ quiz.name }}
              </h1>
              <h2 class="subtitle">
                XXXX
              </h2>

              <div class="tags has-addons">
                <span class="tag">Category</span>
                <span class="tag is-warning">
                  {{ quiz.categoryName }}
                </span>
              </div>
            </section>

            <section class="column is-one-quarter">
              <img :src="quiz.promo" alt=""/>
            </section>
          </section>
        </div>
      </div>
    </section>

    <hr/>

    <question-list
      :questions="quiz.questions"
    ></question-list>

    <hr/>

    <section class="message is-primary" v-if="isDisplayResults">
      <section class="message-header">
        <p>Congratulations!</p>
      </section>
      <section class="message-body">
        <p class="subtitle">
          Score: {{ getScore() }} / {{ maxScore }}
        </p>
      </section>
    </section>

    <div v-else>
      <div class="buttons">
        <button class="button is-primary" @click="displayResults()">
          Display results!
        </button>
      </div>
    </div>

  </section>
</template>

<script>
  import QuestionList from './question-list.vue';

  export default {
    name: 'QuizDetails',
    props: {
      quiz: Object
    },
    components: {
      QuestionList
    },
    computed: {
      isDisplayResults() {
        return this.$store.getters.isDisplayResults;
      },
      score() {
        return this.$store.getters.score;
      },
      maxScore() {
        return this.$store.getters.quiz.questions.length;
      }
    },
    methods: {
      displayResults() {
        this.$store.commit('displayResults');
      },
      getScore() {
        return this.$store.getters.quiz.questions.reduce((score, q) => {
          const isCorrect = (q.correctAnswerIndex === q.userAnswerIndex);
          if (isCorrect) {
            score++;
          }
          return score;
        }, 0);
      }
    }
  }
</script>
