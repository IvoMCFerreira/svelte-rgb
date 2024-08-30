<script>
	import ColorDisplay from "./components/ColorDisplay.svelte";
	import ColorInfo from "./components/ColorInfo.svelte";
	import BitButtons from "./components/BitButtons.svelte";

	let bits = Array(24).fill(0);

	function toggleBit(index) {
		bits = bits.map((bit, i) => (i === index ? 1 - bit : bit));
	}

	function getHexColor() {
		const binaryString = bits.join('');
		const r = parseInt(binaryString.slice(0, 8), 2);
		const g = parseInt(binaryString.slice(8, 16), 2);
		const b = parseInt(binaryString.slice(16, 24), 2);
	return `#${r.toString(16).padStart(2, '0')}${g.toString(16).padStart(2, '0')}${b.toString(16).padStart(2, '0')}`.toUpperCase();
	}

	function getBinaryString() {
		return `${bits.slice(0, 8).join('')}.${bits.slice(8, 16).join('')}.${bits.slice(16, 24).join('')}`;
	}

	const color = getHexColor();
	const hexColor = color;
	const binaryString = getBinaryString();
</script>

<main>
	<h1>Color Converter</h1>
	<ColorDisplay color={color} />
	<ColorInfo hexColor={hexColor} binaryString={binaryString} />
	<BitButtons bits={bits} toggleBit={toggleBit} />
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