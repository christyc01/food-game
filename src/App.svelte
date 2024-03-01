<script>
	import Dashboard from "./components/Dashboard.svelte";
	import { count } from "../src/stores";
	import ImageAndQuestions from "./components/ImageAndQuestions.svelte";
</script>

<main>
	<div class="screen">
		<Dashboard {count} />
		<ImageAndQuestions {count} />
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

	.screen {
		display: flex;
		position: absolute;
		height: 100%;
		width: 100%;
		top: 0;
	}
</style>
