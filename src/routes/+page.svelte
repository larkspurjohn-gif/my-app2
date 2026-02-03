<script>
    import Button from './Button.svelte' ;
    import {onMount} from 'svelte';
    
    ///task 1
    function handleSave() {
        console.log('Saved!');
    }

    function handleDelete() {
        console.log('Deleted!');
    }

    function handleSubmit() {
        console.log('Submitted!');
    }

    ///task 2
    let items = ['Go-Go Squeeze', 'Tissue', 'Granola Bars', 'Pads', 'Ginger Ale'];

    ///task 3
    let loading = true;
    let error = null;
    let facts = [];
    onMount(async () => {
  try {
    const response = await fetch("https://catfact.ninja/facts");
    if (!response.ok) {
      throw new Error(`Response status: ${response.status}`);
    }

    const data = await response.json();
    facts = data.data;
    console.log(facts);
  } catch (err) {
    error = err.message;
  } finally {
    loading = false;
  }
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

<div class= "cat-facts">
    {#if loading}
        <p class="text-gray-500">Loading cat facts…</p>
    {/if}
     {#if error}
        <p class="text-red-500">Troubling loading cat facts, Error: {error}</p>
    {/if}
    {#if !loading && !error}
        <h1>Cat Facts</h1>
        <ul class="list-disc pl-6 space-y-2">
            {#each facts as item}
                <li>{item.fact}</li>
            {/each}
        </ul>
    {/if}


</div>




