<script>
  export let bits = [];
  export let toggleBit = () => {};
</script>

<div class="buttons">
  {#each bits as bit, i}
    <!-- Button for each bit -->
    <div
      class="button {bit === 1 ? 'on' : ''}"
      on:click={() => toggleBit(i)}
      on:keydown={() => {}}
    ></div>

    <!-- Divider after every 8th bit, but not after the last group -->
    {#if (i + 1) % 8 === 0 && i < bits.length - 1}
      <div class="divider"></div>
    {/if}
  {/each}
</div>

<style>
  .buttons {
    display: flex;
    justify-content: center;
    gap: 10px;
    align-items: center;
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

  .divider {
    width: 8px;
    height: 8px;
    background-color: #000000;
    border-radius: 50%;
    margin: 0 5px;
  }
</style>
