<template>
	<div class="content-box-border">
		<div class="content-box">
			<div class="question"> 
				<h2>{{currentQuestion.question}} </h2>
			</div> 
			<ul v-for="(answer,i) in answers" :key="i">
				<li class="answers">
					{{answer}}
				</li>
			</ul>
			<button class="answer-btn">
				Submit
			</button>
			<button @click ="next" class="next-btn">
				Next
			</button>
		</div>
	</div>
</template>
<script>
	export default {
		props : {
			currentQuestion: Object,
			next: Function
		},
		computed: {
			answers() {
				let answers = [...this.currentQuestion.incorrect_answers]
				answers.push(this.currentQuestion.correct_answer)
				return answers
			}
		},
		mounted() {
			console.log(this.currentQuestion);
		}
	}
</script>