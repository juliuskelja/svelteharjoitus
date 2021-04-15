<script>
  import Modal from './Modal.svelte';
  import Painike from './Painikkeet.svelte';

  import { createEventDispatcher } from 'svelte';
  const dispatch = createEventDispatcher();

  let uusiLemmikki = {
    nimi: '',
    kuvaus: '',
    omistaja: '',
  };

  const peruuta = () => dispatch('peruuta');
  const uusielain = () => dispatch('uusielain', uusiLemmikki);

  const onkoValidi = (teksti) => teksti.trim().length > 0;
  $: validiNimi = onkoValidi(uusiLemmikki.nimi);
  $: validiKuvaus = onkoValidi(uusiLemmikki.kuvaus);
  $: validiOmistaja = onkoValidi(uusiLemmikki.omistaja);

  let virheviesti = 'Kaikki kentät ovat pakollisia!';
</script>

<Modal>
  <h1 slot="header">Uusi lemmikki</h1>

  <p>
    Nimi: <input
      type="text"
      bind:value={uusiLemmikki.nimi}
      class:tyhja={!validiNimi}
    />
  </p>
  <p>
    Kuvaus: <input
      type="text"
      bind:value={uusiLemmikki.kuvaus}
      class:tyhja={!validiKuvaus}
    />
  </p>
  <p>
    Omistaja: <input
      type="text"
      bind:value={uusiLemmikki.omistaja}
      class:tyhja={!validiOmistaja}
    />
  </p>

  <p slot="footer">
    {#if !validiNimi || !validiKuvaus || !validiOmistaja}
      <p class="virhe">{virheviesti}</p>
    {/if}

    <button
      class:tyhja={!validiNimi || !validiKuvaus || !validiOmistaja}
      disabled={!validiNimi || !validiKuvaus || !validiOmistaja}
      on:click={uusielain}>Tallenna</button
    >
    <Painike on:click={peruuta}>Peruuta</Painike>
  </p>
</Modal>

<style>
  button {
    border: 1px dotted black;
    font-family: Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;
    letter-spacing: 2px;
  }
  .virhe {
    color: red;
  }
</style>
