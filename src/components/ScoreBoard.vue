<template>
  <div class="scoreboard">
    <div class="wrong">
      <strong>{{ wrong }}</strong>
      <span>Wrong</span>
    </div>
    <div class="correct">
      <strong>{{ correct }}</strong>
      <span>Correct</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "ScoreBoard",
  props: ["isCorrect"],
  data() {
    return {
      wrong: 0,
      correct: 0
    };
  },
  watch: {
    isCorrect(val) {
      if (val === null || val === undefined) return;
      if (val) ++this.correct;
      else ++this.wrong;
    }
  }
};
</script>
