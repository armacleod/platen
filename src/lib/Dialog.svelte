<script>
  let { title = '', open = $bindable(false), children } = $props();
</script>

{#if open}
  <div class="veil" onclick={() => (open = false)}>
    <div class="sheet" role="dialog" aria-modal="true" aria-label={title} onclick={(e) => e.stopPropagation()}>
      {#if title}<h2>{title}</h2>{/if}
      {@render children?.()}
      <div class="actions">
        <button class="btn" onclick={() => (open = false)} type="button">Close</button>
      </div>
    </div>
  </div>
{/if}

<style>
  .veil {
    position: fixed;
    inset: 0;
    background: var(--overlay);
    display: grid;
    place-items: center;
    padding: var(--s-05);
    z-index: 50;
  }

  .sheet {
    background: var(--bg);
    color: var(--fg);
    border: 1px solid var(--border-strong);
    padding: var(--s-06);
    width: min(28rem, 100%);
  }

  h2 {
    font: var(--type-heading);
    margin: 0 0 var(--s-04);
  }

  .actions {
    margin-top: var(--s-05);
    display: flex;
    justify-content: flex-end;
  }

  .btn {
    min-height: var(--s-08);
    padding: 0 var(--s-05);
    border: var(--rule);
    background: var(--bg);
    color: var(--fg);
    font: var(--type-ui);
    font-weight: 600;
    cursor: pointer;
  }
</style>
