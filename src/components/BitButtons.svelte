<script>
    export let bits = [];
    export let toggleBit = () => {};
</script>
  
<div class="buttons">
    {#each bits as bit, i}
      <!-- svelte-ignore a11y-click-events-have-key-events -->
      <div
        class="button {bit === 1 ? 'on' : ''}"
        on:click={() => toggleBit(i)}
      ></div>
    {/each}
</div>
  
<style>
    .buttons {
      display: flex;
      justify-content: center;
      gap: 10px;
    }
  
    .button {
      width: 30px;
      height: 30px;
      background-color: #ffffff;
      border-radius: 50%;
      cursor: pointer;
    }
  
    .button.on {
      background-color: #000000;
    }
</style>