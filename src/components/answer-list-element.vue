<template>
  <section
    v-if="answer" @click="onClick()" :class="getCSSClass()"
  >

    <p>
      {{ answer }}
    </p>

  </section>
</template>

<script>
  export default {
    name: 'AnswerListElement',
    props: {
      answer: String,
      answerIndex: Number,
      question: Object
    },
    data() {
      return {
        displayStyle: {
          select: false,
          good: false,
          bad: false
        }
      };
    },
    computed: {
      isDisplayResults() {
        return this.$store.getters.isDisplayResults;
      }
    },
    methods: {
      onClick() {
        this.$emit('selectAnswer', this.answer);
        this.markAsSelect();
      },
      markAsSelect() {
        this.displayStyle.select = true;
      },
      markAsUnSelect() {
        this.displayStyle.select = false;
      },
      markAsGood() {
        this.markAsUnSelect();
        this.displayStyle.good = true;
      },
      markAsBad() {
        this.markAsUnSelect();
        this.displayStyle.bad = true;
      },
      getCSSClass() {
        return {
          'is-selected': this.displayStyle.select,
          'is-good': this.displayStyle.good,
          'is-bad': this.displayStyle.bad
        }
      }
    },
    watch: {
      isDisplayResults(value) {
        if (!value) {
          return;
        }

        const q = this.question;
        const isUserCorrectAnswer = (this.answerIndex === q.correctAnswerIndex);
        const isUserSelectCorrectAnswer = (q.correctAnswerIndex === q.userAnswerIndex);
        const isUserSelectThisAnswer = (this.answerIndex === q.userAnswerIndex);

        if (isUserSelectThisAnswer) {
          if (isUserSelectCorrectAnswer) {
            this.markAsGood();
          } else {
            this.markAsBad();
          }
        }

        if (isUserCorrectAnswer) {
          this.markAsGood();
        }
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

  section.is-selected {
    background: yellow;
  }

  section.is-good {
    background: green;
  }

  section.is-bad {
    background: red;
  }
</style>
