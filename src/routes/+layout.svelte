<script lang="ts" context="module">
  import '../i18n.js';
  import '../app.css';
</script>

<script lang="ts">
  import { _, isLoading } from 'svelte-i18n';

  import LocaleSwitcher from '$lib/locale-switcher/LocaleSwitcher.svelte';
  import Waiting from '$lib/waiting/Waiting.svelte';
</script>

{#if $isLoading}
  <Waiting />
{:else}
  <LocaleSwitcher />

  <nav>
    <a href="/">{$_('nav.home')}</a>
    <a href="/about">{$_('nav.about')}</a>
    <a href="/settings">{$_('nav.settings')}</a>
  </nav>

  <main>
    <slot />
  </main>
{/if}
