<script lang="ts">
  import { _, locale, locales } from 'svelte-i18n';

  const getLanguageName = (lang: string) => {
    return new Intl.DisplayNames([lang], { type: 'language' }).of(lang);
  };
</script>

<div class="locale-selector">
  <select bind:value={$locale}>
    {#each $locales as locale}
      <option value={locale}>{getLanguageName(locale)}</option>
    {/each}
  </select>
</div>
