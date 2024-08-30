<script>
	// Initialize the array representing binary bits
	let bits = Array(24).fill(0);
  
	// Toggle the bit at the given index
	function toggleBit(index) {
	  bits = bits.map((bit, i) => (i === index ? 1 - bit : bit));
	}
  
	// Convert the bits to hexadecimal color
	function getHexColor() {
	  const binaryString = bits.join('');
	  const r = parseInt(binaryString.slice(0, 8), 2);
	  const g = parseInt(binaryString.slice(8, 16), 2);
	  const b = parseInt(binaryString.slice(16, 24), 2);
	  const hexColor = `#${r.toString(16).padStart(2, '0')}${g.toString(16).padStart(2, '0')}${b.toString(16).padStart(2, '0')}`;
	  return hexColor.toUpperCase();
	}
  
	// Display the binary string in groups of 8 bits
	function getBinaryString() {
	  return `${bits.slice(0, 8).join('')}.${bits.slice(8, 16).join('')}.${bits.slice(16, 24).join('')}`;
	}
  </script>
  
  <style>
	body {
	  background-color: #F8B8B8;
	  color: #FFFFFF;
	  display: flex;
	  justify-content: center;
	  align-items: center;
	  height: 100vh;
	  margin: 0;
	  font-family: Arial, sans-serif;
	}
  
	.app-container {
	  text-align: center;
	}
  
	.color-box {
	  width: 200px;
	  height: 200px;
	  border-radius: 8px;
	  margin-bottom: 20px;
	}
  
	.hex, .binary {
	  font-size: 20px;
	  margin-bottom: 20px;
	  color: #FFFFFF;
	}
  
	.buttons {
	  display: flex;
	  justify-content: center;
	  gap: 10px;
	}
  
	.button {
	  width: 30px;
	  height: 30px;
	  background-color: #CCCCCC;
	  border-radius: 50%;
	  cursor: pointer;
	}
  
	.button.on {
	  background-color: #000000;
	}
  </style>
  
  <div class="app-container">
	<div class="color-box" style="background-color: {getHexColor()};"></div>
  
	<div class="hex">Hex: {getHexColor()}</div>
	<div class="binary">Binary: {getBinaryString()}</div>
  
	<div class="buttons">
	  {#each bits as bit, i}
		<div
		  class="button {bit === 1 ? 'on' : ''}"
		  on:click={() => toggleBit(i)}
		></div>
	  {/each}
	</div>
  </div>
  