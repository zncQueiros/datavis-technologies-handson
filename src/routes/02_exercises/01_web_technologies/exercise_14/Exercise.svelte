<script>
  let current = "";
</script>

<!-- We will cover buttons later on! -->
<button class="btn" on:click={() => (current = "messi")} class:btn2={current=="messi"}>
  Messi 
</button>

<button class="btn" on:click={() => (current = "ronaldo")} class:btn2={current=="ronaldo"}>
  Ronaldo
</button>

<button class="btn" on:click={() => (current = "neymar")} class:btn2={current=="neymar"}>
  Neymar
</button>

<style>
  button.btn{
    background-color: darkgrey;
  }
  button.btn2 {
    background-color: aquamarine;
  }
</style>
