<script lang="ts">
  import { bind } from "svelte/internal";

  let counter = 2;
  let cantidad = 3;

  // const agregar = () => {
  //   counter = counter + cantidad;
  // };
  // const quitar = () => {
  //   counter = counter - cantidad;
  // };

  const calcular = (cantidad) => {
    counter = counter += cantidad;
  };

  const resetear = () => {
    counter = 0;
    cantidad = 0;
  };
</script>

<main>
  <h2>agregar la cantidad de:</h2>
  <input class="input" type="number" bind:value={cantidad} />
  <div>
    <p class={counter < 0 ? "bajoCero" : "sobreCero"}>{counter}</p>
    <button class="logo" on:click={() => calcular(cantidad)}
      >Agregar +{cantidad}</button
    >

    <button class="logo svelte" on:click={() => calcular(-cantidad)}
      >Quitar -{cantidad}</button
    >
  </div>
  <div>
    <button class="logo svelte2" on:click={resetear}>Reset</button>
  </div>
</main>

<style>
  input {
    font-size: 4em;
    width: 100px;
    margin: 20px;
    padding: 10px;
  }
  p {
    font-size: 4em;
  }
  .logo {
    height: 6em;
    padding: 1.5em;
    will-change: filter;
    font-size: 2rem;
  }
  .logo:hover {
    filter: drop-shadow(0 0 2em #646cffaa);
  }
  .logo.svelte:hover {
    filter: drop-shadow(0 0 2em #ff3e00aa);
  }
  .logo.svelte2:hover {
    filter: drop-shadow(0 0 2em #58e7c8aa);
  }
  div {
    padding-top: 1em;
  }
  .bajoCero {
    color: red;
  }
  .sobreCero {
    color: white;
  }
</style>
