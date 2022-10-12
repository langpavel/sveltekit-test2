<script lang="ts">
  import Waiting from '$lib/waiting/Waiting.svelte';

  export let disabled: boolean = false;
  export let title: string | undefined = undefined;
  export let delay: number = 0;

  export let onclick: (
    ev: MouseEvent & { currentTarget: EventTarget & HTMLButtonElement },
  ) => Promise<any>;

  let pending: boolean = false;
  let error: any = null;
  let derivedTitle: string | undefined = title;

  const click = async (
    event: MouseEvent & {
      currentTarget: EventTarget & HTMLButtonElement;
    },
  ) => {
    pending = true;
    error = null;
    derivedTitle = 'Waiting';
    try {
      await onclick(event);
      pending = false;
      derivedTitle = title || 'OK';
    } catch (err) {
      pending = false;
      error = err;
      derivedTitle = `${err}`;
    }
  };
</script>

<pre>
Pend: {pending}
dis: {disabled}
err: {error}
</pre>

<button on:click={click} disabled={disabled || pending} title={derivedTitle}>
  <slot />
  {#if pending}
    <Waiting {delay} />
  {/if}
  {#if error}
    <span>❌</span>
  {/if}
</button>
