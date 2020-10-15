<template>
	<div :class="['result-modal', isCorrect ? 'isCorrect' : 'is-wrong']">
		<div class="overlay"></div>
		<div class="result-modal-content">
			<h3 v-if="isCorrect">
				👊👊👊
				<br />
        YOU WON!
      </h3>
				<h3 v-else>
					😟😢😟
					<br />
        YOU LOST!
      </h3>
					<div v-if="isCorrect" class="correct-answer">
						<small>The correct answer was:</small>
						<br />
						<strong v-html="question.correct_answer"></strong>
					</div>
					<button @click="$emit('nextQuestion')">Go to next question 👉</button>
		</div>
	</div>
</template>
<script>
	export default {
  name: "ResultModal",
  props: ["question", "isCorrect"],
  data() {
    return {};
  }
};
</script>