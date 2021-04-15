<script>
  export let name;
  import Otsikko from './LemmikkiInfo.svelte';
  import Vinkit from './Hoitovinkit.svelte';
  import Painike from './Painikkeet.svelte';
  import Lemmikit from './Lemmikit.svelte';
  import UusiElain from './UusiElain.svelte';

  let nakyvyysAika = 3000;

  const elain = {
    haku: 'pet rat',
    laji: 'Rotta',
  };

  let lemmikki = {
    nimi: '',
    kuvaus: '',
    omistaja: '',
  };

  const lisaa = (ce) => {
    lemmikit.push(ce.detail);
    lemmikit = lemmikit;
  };

  const poistaLemmikki = (ce) => {
    lemmikit = lemmikit.filter((x) => x.nimi !== ce.detail);
  };

  let lemmikit = [
    {
      nimi: 'Make',
      kuvaus: 'nälkäinen ja väsynyt',
      omistaja: 'Black Mage',
    },
    {
      nimi: 'Hugo',
      kuvaus: 'leikkisä ja energinen',
      omistaja: 'Hörökorva Heikki',
    },
    {
      nimi: 'Roni',
      kuvaus: 'herkkusuu, joka tekee reikiä vaatteisiin',
      omistaja: 'Pikku-Piki',
    },
  ];

  const lisaaUusi = () => (piilotaTiedot = !piilotaTiedot);
  let piilotaTiedot = false;

  const peruuta = () => {
    piilotaTiedot = false;
  };
</script>

<main>
  <h1><Otsikko {name} /></h1>
  <h3><Vinkit {nakyvyysAika} /></h3>

  <Lemmikit {lemmikit} {...elain} on:poista={poistaLemmikki} />

  {#if piilotaTiedot}
    <UusiElain on:peruuta={peruuta} on:uusielain={lisaa} />
  {/if}
  <p><Painike on:click={lisaaUusi}>Lisää uusi</Painike></p>
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    font-size: 4em;
    font-weight: 100;
    letter-spacing: 5px;
  }

  h3 {
    font-style: italic;
    letter-spacing: 2px;
    padding-top: 2em;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
