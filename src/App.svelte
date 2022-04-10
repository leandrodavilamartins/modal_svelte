<script>
  import Modal from "./Modal.svelte";

  let todos = [];
  let item;
  let quant;

  function add() {
    todos = [...todos, ""];
  }

  let formulaModalOpen = false;
  let misturaModalOpen = false;

  $: console.log(item);
  $: console.log(quant);
</script>

<main>
  <button class="btn btn-warning" on:click={() => (formulaModalOpen = true)}
    >Fórmula</button
  >
  <button class="btn btn-warning" on:click={() => (misturaModalOpen = true)}
    >Mistura</button
  >
  <Modal
    open={formulaModalOpen}
    onClosed={() => (formulaModalOpen = false)}
    title="Fórmula"
  >
    {#each todos as todo, index}
      <div class="form-line">
        <input type="text" placeholder="Matéria-prima" bind:value={item} />
        <input type="number" placeholder="Quantidade" bind:value={quant} />
        <button class="btn btn-danger">X</button>
      </div>
    {/each}
    <div>
      <br />
      <button class="btn btn-warning" on:click={add}>Adicionar</button>
    </div>
  </Modal>

  <Modal
    open={misturaModalOpen}
    onClosed={() => (misturaModalOpen = false)}
    title="Mistura"
  />
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
  .form-line {
    display: block;
  }
  input {
    background-color: #212529;
    color: whitesmoke;
  }
</style>
