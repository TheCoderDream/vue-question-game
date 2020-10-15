<template>
  <div class="question">
    <h2 v-html="question.question"></h2>
    <button
      v-for="(answer, index) in answers"
      :key="index"
      @click="$emit('answerQuestion', answer)"
      v-html="answer"
    ></button>
  </div>
</template>
<script>
function shuffle(array) {
  for (let i = array.length - 1; i > 0; i--) {
    let j = Math.floor(Math.random() * (i + 1));
    [array[i], array[j]] = [array[j], array[i]];
  }
}
export default {
  name: "Question",
  props: ["question"],
  data() {
    return {
      answers: []
    };
  },
  methods: {
    setAnswers() {
      if (!this.question) return;
      const answers = [
        ...this.question.incorrect_answers,
        this.question.correct_answer
      ];
      shuffle(answers);
      this.answers = answers;
    }
  },
  watch: {
    question(val, old) {
      this.setAnswers();
    }
  },
  created() {
    this.setAnswers();
  }
};
</script>
