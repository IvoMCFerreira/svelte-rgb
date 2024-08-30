<script>
  export let bits = [];
  export let toggleBit = () => {};

  function toggleOctet(octetIndex) {
    const startIndex = octetIndex * 8;
    const endIndex = startIndex + 8;

    for (let i = startIndex; i < endIndex; i++) {
      toggleBit(i);
    }
  }
</script>

<div class="octets">
  {#each Array(3) as _, octetIndex}
    <div class="octet-group">
      <!-- Binary Display for the current octet -->
      <div class="octet-binary">
        {#each bits.slice(octetIndex * 8, (octetIndex + 1) * 8) as bit, i}
          <span class="binary-bit">{bit}</span>
        {/each}
      </div>
      
      <!-- Bit buttons for the current octet -->
      <div class="buttons">
        {#each bits.slice(octetIndex * 8, (octetIndex + 1) * 8) as bit, i}
          <div
            class="button {bit === 1 ? 'on' : ''}"
            on:click={() => toggleBit(octetIndex * 8 + i)}
            on:keydown={() => {}}
          ></div>
        {/each}
      </div>
      
      <!-- Label for the current octet -->
      <div class="label" on:click={() => toggleOctet(octetIndex)} on:keydown={() => {}}>
        {#if octetIndex === 0}RED{/if}
        {#if octetIndex === 1}GREEN{/if}
        {#if octetIndex === 2}BLUE{/if}
      </div>
    </div>

    {#if octetIndex < 2}
      <div class="divider"></div>
    {/if}
  {/each}
</div>

<style>
  .octets {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 20px;
  }

  .octet-group {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .octet-binary {
    display: flex;
    gap: 10px;
    margin-bottom: 5px;
    justify-content: center; /* Center the binary digits */
  }

  .binary-bit {
    width: 30px; /* Match button width */
    text-align: center;
    font-size: 18px;
    color: #FFFFFF;
  }

  .buttons {
    display: flex;
    gap: 10px;
    margin-bottom: 5px;
  }

  .button {
    width: 30px;
    height: 30px;
    background-color: #ffffff;
    border-radius: 50%;
    cursor: pointer;
  }

  .button.on {
    background-color: #b95b5b;
  }

  .divider {
    width: 8px;
    height: 8px;
    background-color: #000000;
    border-radius: 50%;
    margin: 0 5px;
  }

  .label {
    font-size: 18px;
    font-weight: bold;
    color: #FFFFFF;
    cursor: pointer;
    user-select: none;
    margin-top: 5px;
  }
</style>
