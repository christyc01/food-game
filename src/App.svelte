<script>
	let count = 0;
	let questionNumber = 1;
	let sliderPointer;

	const handleClickA = () => {
		if (count >= 75) {
			alert("You've saved enough money to buy a new car!");
			return;
		}
		count += 5;
		questionNumber += 1;
	};
	const handleClickB = () => {
		if (count <= -25) {
			alert("You've spent too much money on food this month!");
			return;
		}
		count -= 5;
		questionNumber += 1;
	};

	const sliderLinesPositions = [-25, 0, 25, 50, 75];

	$: {
		if (sliderPointer) {
			sliderPointer.style.bottom = `${count + 25}%`;
		}
	}
</script>

<main>
	<div class="screen">
		<div class="dashboard">
			<p class="dollars-saved">${count}</p>
			<p class="dollars-saved-subtext">saved this month</p>
			<div class="slide-container">
				<input
					type="range"
					min="-25"
					max="75"
					value={count}
					class="slider"
					id="myRange"
				/>
				<div class="slider-pointer" bind:this={sliderPointer}></div>
				<div class="slider-lines">
					{#each sliderLinesPositions as position (position)}
						<div
							class="slider-lines-and-amounts"
							style="bottom: {position}%"
						>
							<div class="slider-line"></div>
							<p class="slider-label">${position}</p>
						</div>
					{/each}
				</div>
			</div>
		</div>
		<div class="image">
			<div class="popup-question">
				<h2>Question {questionNumber}</h2>
				<p>What even is food?</p>
				<div class="buttons">
					<button on:click={handleClickA}>Something to eat</button>
					<button on:click={handleClickB}
						>Something to post pictures of on Instagram</button
					>
				</div>
			</div>
		</div>
	</div>
</main>

<style>
	:global(body) {
		margin: 0;
		padding: 0;
		background-color: #fefbda;
		z-index: -2;
	}
	main {
		display: flex;
		justify-content: center;
		align-items: center;
		flex-direction: column;
		z-index: 1;
	}
	button {
		flex-grow: 1;
		background-color: #c4d6d3;
		flex-basis: 0;
	}
	.buttons {
		display: flex;
		gap: 10px;
	}
	.dashboard {
		width: 355px;
		background-color: #485676;
	}
	.dollars-saved {
		color: #ff7c58;
		font-size: 50px;
		font-weight: 800;
		margin: 50px 0px 0px 0px;
	}
	.dollars-saved-subtext {
		color: #fefbda;
		font-size: 15px;
		margin: 0px 0px 50px 0px;
	}
	.image {
		height: 100%;
		width: 100%;
		background-image: url("./assets/kitchen.png");
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
	.screen {
		display: flex;
		position: absolute;
		height: 100%;
		width: 100%;
		top: 0;
	}
	.slide-container {
		position: relative;
		display: flex;
		justify-content: center;
		height: 200px;
	}
	input[type="range"] {
		position: absolute;
		top: 75px;
		transform: rotate(270deg);
		height: 5px;
	}
	.slider {
		-webkit-appearance: none;
		width: 200px;
		background: #ff7c58;
		outline: none;
	}
	.slider-label {
		color: #fefbda;
		font-size: 18px;
		font-weight: 800;
		margin: 0;
		transform: translateY(-10px);
		padding-left: 10px;
	}
	.slider-lines {
		position: relative;
		top: -65px;
		left: 23px;
		width: 50px;
	}
	.slider-line {
		background-color: #ff7c58;
		width: 30px;
	}
	.slider-lines-and-amounts {
		display: flex;
		position: absolute;
		height: 5px;
		transform: translateY(-2.5px);
	}
	.slider::-webkit-slider-thumb {
		-webkit-appearance: none;
		appearance: none;
	}
	.slider::-moz-range-thumb {
		appearance: none;
	}
	.slider-pointer {
		position: absolute;
		width: 0px;
		height: 0px;
		border-left: 25px solid #fefbda;
		border-bottom: 20px solid transparent;
		border-right: 25px solid transparent;
		border-top: 20px solid transparent;
		margin-right: 10px;
	}
</style>
