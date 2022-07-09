<script>
  import { slide } from 'svelte/transition';

  export let name;
  export let type;
  export let files = undefined;
  export let folders = undefined;

  let expanded = false;

  const hasChildren = type === 'folder' 
    && ((files && files.length) || (folders && folders.length));

  const toggle = () => {
    expanded = !expanded;
  };

</script>

<div class="treenode">
  <div class="title" on:click={toggle}>
    {#if type === 'folder'}
      <svg class="icon" class:rotated={type === 'folder' && expanded} width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polyline points="9 18 15 12 9 6"></polyline></svg>
    {:else}
<svg xmlns="http://www.w3.org/2000/svg" width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="#000" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M13 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V9z"></path><polyline points="13 2 13 9 20 9"></polyline></svg>
    {/if}
    { name }
  </div>
  {#if hasChildren && expanded}
    <div class="children" transition:slide={{ duration: 100 }}>
      {#if folders }
        {#each folders as folder}
          <svelte:self {...folder} type="folder" />
        {/each}
      {/if}
      {#if files}
        {#each files as file}
          <svelte:self {...file} type="file" />
        {/each}
      {/if}
    </div>
  {/if}
</div>

<style>
  .treenode {
  }

  .children {
      padding-left: 1.5rem;
  }

  .title {
    color: #000;
    padding: 0.2rem;
  }

  .title:hover,
  .title:focus {
    background: #ddd;
    border-radius: 0.5rem;
  }

  .icon {
    transition: transform 100ms;
  }

  .rotated {
    transform: rotate(90deg);
  }
</style>

