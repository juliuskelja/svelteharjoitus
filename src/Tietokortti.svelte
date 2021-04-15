<script>
  import Painikkeet from './Painikkeet.svelte';
  import { createEventDispatcher } from 'svelte';
  const dispatch = createEventDispatcher();

  export let nimi;
  export let kuvaus;
  export let omistaja;
  export let laji;
  export let haku;
  let arvo;

  const tapahtumaPoista = () => dispatch('poista', nimi);
</script>

<h2>{laji} {nimi}</h2>
<img src="https://loremflickr.com/320/240/{haku}" alt="Rotan kuva" />
<p>{kuvaus}</p>
<p><b>Omistaja: </b>{omistaja}</p>
<Painikkeet on:click={tapahtumaPoista}>Poista</Painikkeet>

<style>
  img {
    border: 3px double black;
    padding: 1px;
  }
  h2 {
    padding-top: 1em;
    letter-spacing: 2px;
    font-family: Georgia, 'Times New Roman', Times, serif;
    font-weight: 100;
    font-size: 2em;
  }
</style>
