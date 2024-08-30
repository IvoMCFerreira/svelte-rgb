<script>
  export let color = '#000000';
  export let hexColor = '#000000';
</script>

<div class="color-box" style="background-color: {color};"></div>
<div class="hex">Hex: {hexColor}</div>

<style>
  .color-box {
    width: 200px;
    height: 200px;
    border-radius: 8px;
    margin-bottom: 10px;
  }

  .hex {
    font-size: 20px;
    font-weight: bold;
    color: #FFFFFF;
    text-align: center;
  }
</style>
