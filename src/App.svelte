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
        id: Math.random(),
        name: name,
        description: description,
        jobTitle: title,
        imageUrl: image
      }
    ];

    formState = "done";
  };

  const deleteFirst = () => {
    // console.log("First");
    createdContactsList = createdContactsList.slice(1);
  };

  const deleteLast = () => {
    // console.log("Last");
    createdContactsList = createdContactsList.slice(0, -1);
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
<button on:click={deleteFirst}>Delete Firs</button>
<button on:click={deleteLast}>Delete Last</button>

{#if formState === 'invalid'}
  <p class="invalidInput">Invalid input! Please complete all the fields!</p>
{:else}
  <p>Please fill all the fields and hit the button!</p>
{/if}

{#each createdContactsList as createdContact, idx (createdContact.id)}
  <h1># {idx + 1}</h1>
  <ContactCard
    userName={createdContact.name}
    jobTitle={createdContact.jobTitle}
    description={createdContact.description}
    userImage={createdContact.imageUrl} />
{:else}
  <p>Please start adding contacts!</p>
{/each}
