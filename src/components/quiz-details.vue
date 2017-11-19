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
    }
  }
</script>
