<script>
  import Tiedot from './Tietokortti.svelte';
  export let lemmikit;
  export let haku;
  export let laji;
</script>

{#each lemmikit as elukka}
  <Tiedot {haku} {laji} {...elukka} on:poista />
{/each}
