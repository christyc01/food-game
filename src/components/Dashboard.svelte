<script>
	export let count;
	let sliderPointer;
	const sliderLinesPositions = [-25, 0, 25, 50, 75];

	$: {
		if (sliderPointer) {
			sliderPointer.style.bottom = `${$count + 25}%`;
		}
	}
</script>

<div class="dashboard">
	<p class="dollars-saved">${$count}</p>
	<p class="dollars-saved-subtext">saved this month</p>
	<div class="slide-container">
		<input
			type="range"
			min="-25"
			max="75"
			value={$count}
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

<style>
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
