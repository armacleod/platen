<script>
  let { tabs = [], value = $bindable('') } = $props();
  $effect(() => {
    if (!value && tabs.length) value = tabs[0].id;
  });
</script>

<div class="platen-tabs" role="tablist" aria-label="Sections">
  {#each tabs as t}
    <button
      role="tab"
      aria-selected={value === t.id}
      class:active={value === t.id}
      onclick={() => (value = t.id)}
      type="button"
    >{t.label}</button>
  {/each}
</div>

<style>
  .platen-tabs {
    display: flex;
    gap: 0;
    border-bottom: var(--rule-strong);
  }

  button {
    appearance: none;
    background: transparent;
    border: 0;
    border-bottom: 2px solid transparent;
    margin-bottom: -1px;
    padding: var(--s-03) var(--s-05);
    min-height: var(--s-08);
    font: var(--type-label);
    letter-spacing: 0.06em;
    text-transform: uppercase;
    color: var(--fg-subtle);
    cursor: pointer;
  }

  button:hover {
    color: var(--fg);
  }

  .active {
    color: var(--accent);
    border-bottom-color: var(--accent-fill);
  }

  button:focus-visible {
    outline: 2px solid var(--focus);
    outline-offset: 2px;
  }
</style>
