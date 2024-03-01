<script>
	import data from "../data/questions-and-answers.json";

	export let count;
	let showQuestion;
	let questionNumber = 1;
	let showAnswer;
	let toggleAnswerOn = false;

	const handleClickA = () => {
		if ($count >= 75) {
			alert("You've saved enough money to buy a new car!");
			return;
		}
		toggleAnswerOn = true;
		count.update((n) => n + 5);
	};
	const handleClickB = () => {
		if ($count <= -25) {
			alert("You've spent too much money on food this month!");
			return;
		}
		toggleAnswerOn = true;
		count.update((n) => n - 5);
	};

	const handleClickNext = () => {
		if (questionNumber <= data.length - 1) {
			toggleAnswerOn = false;
			questionNumber += 1;
		} else {
			alert("You've answered all the questions!");
		}
	};

	$: {
		if (toggleAnswerOn && showAnswer && showQuestion) {
			showAnswer.style.display = "block";
			showQuestion.style.display = "none";
		} else if (!toggleAnswerOn && showAnswer && showQuestion) {
			showAnswer.style.display = "none";
			showQuestion.style.display = "block";
		}
	}
</script>

<div class="image-and-questions">
	<div class="popup-question" bind:this={showQuestion}>
		<h2>Question {questionNumber}</h2>
		<p>{data[questionNumber - 1].question}</p>
		<div class="buttons">
			<button on:click={handleClickA}
				>{data[questionNumber - 1].optionA}</button
			>
			<button on:click={handleClickB}
				>{data[questionNumber - 1].optionB}</button
			>
		</div>
	</div>
	<div class="popup-answer" bind:this={showAnswer}>
		<!-- TODO: Show answerA or B, depending on the option selected -->
		<h2>{@html data[questionNumber - 1].answerA.split(/\\n/g)[0]}</h2>
		<p>
			{@html data[questionNumber - 1].answerA.split(/\\n/g)[1]
				? data[questionNumber - 1].answerA
						.split(/\\n/g)[1]
						.replace(/\\n/g, "<br>")
				: ""}
		</p>

		<div class="buttons">
			<button on:click={handleClickNext}>Next</button>
		</div>
	</div>
</div>

<style>
	button {
		flex-grow: 1;
		background-color: #c4d6d3;
		flex-basis: 0;
	}
	.buttons {
		display: flex;
		gap: 10px;
	}

	.image-and-questions {
		height: 100%;
		width: 100%;
		background-image: url("../assets/kitchen.png");
		background-size: contain;
		background-repeat: no-repeat;
		background-position: center;
		display: flex;
		justify-content: center;
		align-items: center;
	}
	.popup-question {
		position: absolute;
		background-color: #ffa68a;
		opacity: 0.95;
		padding: 20px;
		border-radius: 10px;
		box-shadow: 0 0 10px 0 rgba(0, 0, 0, 0.1);
	}
	.popup-answer {
		display: none;
		position: absolute;
		background-color: #ffa68a;
		opacity: 0.95;
		padding: 20px;
		border-radius: 10px;
		box-shadow: 0 0 10px 0 rgba(0, 0, 0, 0.1);
	}
</style>
