<script>
  /** @type {'primary' | 'secondary' | 'ghost' | 'danger'} */
  let { variant = 'primary', size = 'md', disabled = false, type = 'button', children, onclick } = $props();
</script>

<button class={['platen-btn', variant, size]} {type} {disabled} {onclick}>
  {@render children?.()}
</button>

<style>
  .platen-btn {
    appearance: none;
    display: inline-flex;
    align-items: center;
    justify-content: center;
    gap: var(--s-03);
    border-radius: var(--r-1);
    border: 1px solid transparent;
    font: var(--type-ui);
    font-weight: 600;
    letter-spacing: 0.01em;
    cursor: pointer;
    min-height: var(--s-08);
    padding: 0 var(--s-05);
    transition:
      background-color var(--t-fast) var(--ease-out),
      border-color var(--t-fast) var(--ease-out),
      color var(--t-fast) var(--ease-out);
  }

  .sm {
    min-height: 1.75rem;
    padding: 0 var(--s-04);
    font-size: 0.8125rem;
  }

  .lg {
    min-height: 3rem;
    padding: 0 var(--s-06);
    font-size: 1rem;
  }

  .primary {
    background: var(--button-primary-bg);
    color: var(--button-primary-fg);
  }

  .primary:hover:not(:disabled) {
    background: var(--button-primary-hover);
  }

  .primary:active:not(:disabled) {
    background: var(--button-primary-active);
  }

  .secondary {
    background: transparent;
    color: var(--fg);
    border-color: var(--border-strong);
  }

  .secondary:hover:not(:disabled) {
    background: var(--bg-subtle);
  }

  .ghost {
    background: transparent;
    color: var(--accent);
    border-color: var(--border);
  }

  .ghost:hover:not(:disabled) {
    border-color: var(--accent);
    background: var(--accent-muted);
  }

  .danger {
    background: var(--button-danger-bg);
    border-color: var(--button-danger-bg);
    color: var(--button-danger-fg);
  }

  .danger:hover:not(:disabled) {
    background: var(--button-danger-hover);
    border-color: var(--button-danger-hover);
    color: #fff;
  }

  .danger:active:not(:disabled) {
    background: var(--button-danger-active);
    border-color: var(--button-danger-active);
    color: #fff;
  }

  :disabled {
    opacity: 0.45;
    cursor: not-allowed;
  }
</style>
