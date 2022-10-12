<script lang="ts">
  import { onMount } from 'svelte';
  import { fade } from 'svelte/transition';

  export let delay: number = 600;

  let visible = false;

  onMount(() => {
    const interval = globalThis.setTimeout(() => {
      visible = true;
    }, delay);

    return () => {
      globalThis.clearInterval(interval);
    };
  });
</script>

{#if visible}
  <span in:fade>
    <slot>⌛</slot>
  </span>
{:else}
  <span>{' '}</span>
{/if}
