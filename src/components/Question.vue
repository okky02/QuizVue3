<script setup>
import { defineProps } from 'vue';

const emit = defineEmits(['selectOption']);
const { question } = defineProps(['question']);

const emitSelectedOption = (option) => {
	emit('selectOption', option);
};
</script>

<template>
	<section id="question-container">
		<h1 class="question">{{ question.text }}</h1>
	</section>
	<section id="options-container">
		<div
			v-for="option in question.answers"
			:key="option.id"
			class="option"
			@click="emitSelectedOption(option)"
		>
			<p class="option-label">{{ option.label }}.</p>
			<div class="option-value">{{ option.text }}</div>
		</div>
	</section>
</template>

<style scoped>
#quiz-container {
	margin-top: 20px;
}

.question {
	font-size: 40px;
	margin-bottom: 20px;
}

.option {
	display: flex;
	align-items: center;
	cursor: pointer;
	height: 50px;
	margin-bottom: 10px;
}

.option-label {
	font-size: 30px;
	width: 50px;
	height: 50px;
	background-color: #a0ced9;
	display: flex;
	align-items: center;
	justify-content: center;
}

.option-value {
	background-color: #e2e2e2;
	width: 100%;
	font-size: 30px;
	padding: 0 20px;
	height: 50px;
	display: flex;
	align-items: center;
}
</style>
