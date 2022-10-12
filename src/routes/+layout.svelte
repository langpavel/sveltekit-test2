<script lang="ts" context="module">
  import { waitLocale } from 'svelte-i18n';

  import '../i18n.js';

  export async function preload() {
    // awaits for the loading of the dictionaries
    return waitLocale();
  }
</script>

<script lang="ts">
  import { _, isLoading } from 'svelte-i18n';

  import '../app.css';
</script>

<!-- {#if !$isLoading} -->
<nav>
  <a href="/">{$_('nav.home')}</a>
  <a href="/about">{$_('nav.about')}</a>
  <a href="/settings">{$_('nav.settings')}</a>
</nav>

<main>
  <slot />
</main>
<!-- {/if} -->
