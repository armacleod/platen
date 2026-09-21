<script>
  /** @type {'info' | 'danger' | 'success'} */
  let { tone = 'info', title = '', children } = $props();
</script>

<div class={['platen-notice', tone]} role={tone === 'danger' ? 'alert' : 'status'}>
  <span class="bar" aria-hidden="true"></span>
  <div>
    {#if title}<strong>{title}</strong>{/if}
    {@render children?.()}
  </div>
</div>

<style>
  .platen-notice {
    display: grid;
    grid-template-columns: 4px 1fr;
    gap: var(--s-04);
    align-items: start;
    border: var(--rule);
    background: var(--bg-raised);
    padding: var(--s-04) var(--s-05);
    font: var(--type-ui);
    min-width: 0;
  }

  .bar {
    background: var(--struct);
    align-self: stretch;
    min-height: 100%;
  }

  .danger .bar {
    background: var(--danger);
  }

  .success .bar {
    background: var(--success);
  }

  .info .bar {
    background: var(--accent-fill);
  }

  strong {
    font-weight: 600;
    margin-right: 0.35em;
  }
</style>
