<script>
  let name = "Cornel";
  let age = 33;

  $: uppercaseName = name.toUpperCase();

  const incrementAge = () => {
    age += 1;
  };

  const changeName = () => {
    name = "Cornelito";
  };
</script>

<style>
  h1 {
    color: purple;
  }
</style>

<h1>Hello {uppercaseName}, my age is {age}!</h1>
<button on:click={incrementAge}>Change age</button>
<button on:click={changeName}>Change name</button>
