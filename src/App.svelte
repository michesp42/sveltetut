<script>
  import Modal from "./components/Modal.svelte";

  let num = 5;
  let showModal = false;
  let people = [
    { name: "yoshi", beltColor: "black", age: 25, id: 1 },
    { name: "mario", beltColor: "orange", age: 45, id: 2 },
    { name: "luigi", beltColor: "brown", age: 35, id: 3 },
  ];

  function handleClick(e, id) {
    people = people.filter((p) => p.id != id);
    console.log(e);
  }

  function toggleModal() {
    showModal = !showModal;
  }
</script>

<main>
  <Modal
    message="Hey, I'm a prop value."
    isPromo
    {showModal}
    on:click={toggleModal}
  >
    <h3>Add a new person</h3>

    <form>
      <input type="text" placeholder="name" />
      <input type="text" placeholder="belt color" />

      <button>Add person</button>
    </form>
  </Modal>

  <button on:click={toggleModal}>Open modal</button>

  {#if num > 20}
    <p>{num} is greater than 20</p>
  {:else if num > 5}
    <p>{num} is greater than 5</p>
  {:else}
    <p>{num} is not greater than 5</p>
  {/if}

  {#each people as person (person.id)}
    <div>
      <h4>{person.name}</h4>

      {#if person.beltColor === "black"}
        <p>Master Ninja</p>
      {/if}

      <p>{person.age} years old, {person.beltColor} belt</p>
      <button
        on:click={(e) => {
          handleClick(e, person.id);
        }}
      >
        delete
      </button>
    </div>
  {:else}
    <p>There are no people to show ...</p>
  {/each}
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
