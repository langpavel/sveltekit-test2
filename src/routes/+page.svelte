<script>
  import Button from '$lib/button/Button.svelte';

  const handleAsyncClick = () =>
    new Promise((resolve, reject) => {
      globalThis.setTimeout(() => {
        const num = Math.random();
        if (num > 0.5) {
          resolve(num);
        } else {
          reject(new Error(`Chyba ${num}`));
        }
      }, 3000);
    });
</script>

<h1 class="text-3xl font-bold underline">Welcome to SvelteKit with Tailwind!</h1>

<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>

<button on:click={handleAsyncClick}>Simple</button>

<Button onclick={handleAsyncClick} title="Testuj!">Test</Button>
