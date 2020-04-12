<script>
  let name = "Cornel";
  let age = 33;

  $: uppercaseName = name.toUpperCase();

  $: console.log(name);

  $: if (name === "Cornelito") {
    age = 25;
  }

  const incrementAge = () => {
    age += 1;
  };

  const changeName = () => {
    name = "Cornelito";
  };

  const nameInput = event => {
    const updatedName = event.target.value;
    name = updatedName;
  };
</script>

<style>
  h1 {
    color: purple;
  }
</style>

<h1>Hello {uppercaseName}, my age is {age}!</h1>
<button on:click={incrementAge}>Change age</button>
<!-- <button on:click={changeName}>Change name</button> -->
<!-- <input type="text" value={name} on:input={nameInput} /> -->
<input type="text" bind:value={name} />
