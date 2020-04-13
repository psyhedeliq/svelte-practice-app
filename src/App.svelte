<script>
  import ContactCard from "./ContactCard.svelte";

  let name = "Cornel Filip";
  let title = "";
  let image = "";
  let description = "";
  let formState = "empty";
  let createdContactsList = [];

  const addContact = () => {
    if (
      name.trim().length === 0 ||
      title.trim().length === 0 ||
      image.trim().length === 0 ||
      description.trim().length === 0
    ) {
      formState = "invalid";
      return;
    }
    createdContactsList = [
      ...createdContactsList,
      {
        name: name,
        description: description,
        jobTitle: title,
        imageUrl: image
      }
    ];

    formState = "done";
  };
</script>

<style>
  #form {
    width: 30rem;
    max-width: 100%;
  }
  .invalidInput {
    color: red;
  }
</style>

<div id="form">
  <div class="form-control">
    <label for="userName">User Name</label>
    <input type="text" bind:value={name} id="userName" />
  </div>
  <div class="form-control">
    <label for="jobTitle">Job Title</label>
    <input type="text" bind:value={title} id="jobTitle" />
  </div>
  <div class="form-control">
    <label for="image">Image URL</label>
    <input type="text" bind:value={image} id="image" />
  </div>
  <div class="form-control">
    <label for="desc">Description</label>
    <textarea rows="3" bind:value={description} id="desc" />
  </div>
</div>

<button on:click={addContact}>Add Contact Card</button>

{#if formState === 'invalid'}
  <p class="invalidInput">Invalid input!</p>
{:else}
  <p>Please fill all the fields!</p>
{/if}

{#each createdContactsList as createdContact}
  <ContactCard
    userName={createdContact.name}
    jobTitle={createdContact.jobTitle}
    description={createdContact.description}
    userImage={createdContact.imageUrl} />
{/each}
