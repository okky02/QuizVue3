<script setup>
import { defineProps } from 'vue';
import { useRouter } from 'vue-router';

const router = useRouter();
const { quiz } = defineProps(['quiz']);

function goToQuiz() {
	router.push({ name: 'quiz', params: { id: quiz.id } });
}
</script>
<template>
	<div class="card" @click="goToQuiz">
		<img :src="quiz.img" :alt="quiz.title" />
		<div class="card-text">
			<h2>{{ quiz.title }}</h2>
			<p>{{ quiz.questions.length }} Questions</p>
		</div>
	</div>
</template>

<style scoped>
.card {
	width: 270px;
	overflow: hidden;
	border-radius: 2%;
	box-shadow: 1px 1px 10px #00000033;
	margin-bottom: 35px;
	margin-right: 20px;
	cursor: pointer;
}

.card img {
	width: 100%;
	height: 200px;
	object-fit: cover;
	margin: 0;
}
.card .card-text {
	padding: 0 15px;
}

.card .card-text h2 {
	font-weight: bold;
}
</style>
