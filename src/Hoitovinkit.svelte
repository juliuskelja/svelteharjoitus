<script>
  export let nakyvyysAika;
  const vinkit = [
    'Silitä rottaa',
    'Anna rotalle mansikoita',
    'Leikkaa rotalle pala juustoa',
    'Opeta rotalle temppuja',
    'Laula rotalle unilaulu',
  ];
  let i = 0;
  setInterval(function () {
    if (i === vinkit.length - 1) {
      i = 0;
    } else {
      i++;
    }
  }, nakyvyysAika);
</script>

<p>{vinkit[i]}</p>
