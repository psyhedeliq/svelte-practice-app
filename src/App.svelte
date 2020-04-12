<script>
  import ContactCard from "./ContactCard.svelte";

  let userName = "Cornel Filip";
  let age = 33;
  let userImage;
  let jobTitle = "Software Developer";
  let description =
    "I am a self taught developer with a strong passion for technology.";

  $: uppercaseName = name.toUpperCase();

  // $: console.log(name);

  // $: if (name === "Cornelito") {
  //   age = 25;
  // }

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
  const jobTitleInput = event => {
    const updateJobTitle = event.target.value;
    jobTitle = updateJobTitle;
  };

  const descriptionInput = event => {
    const updateDescription = event.target.value;
    description = updateDescription;
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
<input type="text" bind:value={userName} />
<input type="text" bind:value={jobTitle} />
<input type="text" bind:value={userImage} />
<textarea rows="3" bind:value={description} />

<ContactCard {userName} {jobTitle} {description} {userImage} />
