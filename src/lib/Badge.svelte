<script>
  /** @type {'neutral' | 'accent' | 'danger' | 'success'} */
  let { tone = 'neutral', children } = $props();
</script>

<span class={['platen-badge', tone]}>
  {@render children?.()}
</span>

<style>
  .platen-badge {
    display: inline-flex;
    align-items: center;
    min-height: var(--target-min);
    padding: 0 var(--s-03);
    border: var(--rule);
    border-radius: var(--r-full);
    font: var(--type-label);
    letter-spacing: 0.06em;
    text-transform: uppercase;
    color: var(--fg-muted);
    background: var(--bg);
  }

  .accent {
    color: var(--accent);
    border-color: var(--accent);
    background: var(--accent-muted);
  }

  .danger {
    color: var(--danger);
    border-color: var(--danger);
    background: var(--danger-muted);
  }

  .success {
    color: var(--success);
    border-color: var(--success);
    background: var(--success-muted);
  }
</style>
