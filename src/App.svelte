<script>
	import ColorDisplay from "./components/ColorDisplay.svelte";
	import ColorInfo from "./components/ColorInfo.svelte";
</script>

<main>
	<h1>Color Converter</h1>
	<ColorDisplay color="#ffffff" />
	<ColorInfo hexColor="#ffffff" binaryString="11111111.11111111.11111111" />
</main>

<style>
	main {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center; /* Center vertically */
		background-color: #F8B8B8;
		color: #FFFFFF;
		height: 100vh; /* Full viewport height */
		margin: 0; /* Remove default margin */
		font-family: Arial, sans-serif;
	}

	h1 {
		color: #ffffff;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>