<script>
    import Button from './Button.svelte' ;
    import {onMount} from 'svelte';
    import { apiData, dogNames } from './store.js';
    
    function handleSave() {
        console.log('Saved!');
    }

    function handleDelete() {
        console.log('Deleted!');
    }

    function handleSubmit() {
        console.log('Submitted!');
    }

    let items = ['Go-Go Squeeze', 'Tissue', 'Granola Bars', 'Pads', 'Ginger Ale'];

    onMount(async () => {
    fetch("https://dog.ceo/api/breeds/list/all")
    .then(response => response.json())
    .then(data => {
            console.log(data);
        apiData.set(data);
    }).catch(error => {
        console.log(error);
        return [];
    });
    });

</script>

<button id= "my-button" class="bg-blue-500 p-g">Click me updated</button>

<div>
<Button
    label="Save"
    bgColor="success"
    onClick={handleSave}
/>

  <Button
    label="Delete"
    bgColor="danger"
    onClick={handleDelete}
  />

  <Button
    label="Submit"
    bgColor="primary"
    onClick={handleSubmit}
  />
</div>
<div class= "shopping lists">
    <h1 class="font-bold">Shopping list</h1>
    <ul>
        {#each items as item, index}
        <li>{index + 1}. {item}</li>
    {/each}
    </ul>
</div>

<div class= "dogs">
    <h1>Types of Dog</h1>
	<ul>
	{#each $dogNames as dogName}
		<li>{dogName}</li>
	{/each}
	</ul>
</div>

<h1>Welcome to SvelteKit</h1>
<p>Visit <a href="https://svelte.dev/docs/kit">svelte.dev/docs/kit</a> to read the documentation</p>


