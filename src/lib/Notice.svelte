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
    border: var(--rule);
    background: var(--bg-raised);
    padding: var(--s-04) var(--s-05);
    font: var(--type-ui);
  }

  .bar {
    background: var(--struct);
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
    display: block;
    font-weight: 600;
    margin-bottom: var(--s-02);
  }
</style>
