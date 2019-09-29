<script>
  import {
    isNewIssueShortcut
  } from './shortcuts';

  import RepositorySelect from './RepositorySelect.svelte';

  export let repositories;

  let showSelect = false;

  function handleGlobalKey(event) {

    if (isNewIssueShortcut(event)) {
      showSelect = true;

      event.preventDefault();
    }
  }
</script>

<svelte:window on:keydown={ handleGlobalKey } />


{#if showSelect}
  <RepositorySelect
    repositories={ repositories }
    onClose={ () => showSelect = false }
  />
{/if}