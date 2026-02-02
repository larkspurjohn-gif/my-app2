<script>
    export let label= 'Button';
    export let bgColor= 'primary';
    export let onClick= () => {};
</script>

<button
  on:click={onClick}
  class={`px-4 py-2 rounded-lg font-medium text-white
    ${bgColor === 'primary' && 'bg-blue-500 hover:bg-blue-600'}
    ${bgColor === 'success' && 'bg-green-500 hover:bg-green-600'}
    ${bgColor === 'danger' && 'bg-red-500 hover:bg-red-600'}
    hover:opacity-90
    focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-black
    active:scale-95
    transition-all duration-150
  `}
>
  {label}
</button>



