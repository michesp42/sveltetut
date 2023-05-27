<script>
  let firstName = "Jimi";
  let lastName = "Hendrix";
  let beltColor = "black";

  $: fullName = `${firstName} ${lastName}`;
  $: {
    console.log(beltColor);
    console.log(fullName);
  }
</script>

<main>
  <p>{fullName} {beltColor} belt</p>
  <input type="text" bind:value={firstName} />
  <input type="text" bind:value={lastName} />
  <input type="text" bind:value={beltColor} />
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
</style>
