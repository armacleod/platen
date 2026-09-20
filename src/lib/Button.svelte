<script>
  /** @type {'primary' | 'ghost' | 'danger'} */
  let { variant = 'primary', disabled = false, type = 'button', children, onclick } = $props();
</script>

<button class={['quire-btn', variant]} {type} {disabled} {onclick}>
  {@render children?.()}
</button>

<style>
  .quire-btn {
    appearance: none;
    display: inline-flex;
    align-items: center;
    justify-content: center;
    gap: var(--s-03);
    min-height: var(--s-08);
    padding: 0 var(--s-05);
    border-radius: var(--r-1);
    border: 1px solid transparent;
    font: var(--type-ui);
    font-weight: 600;
    letter-spacing: 0.01em;
    cursor: pointer;
    transition:
      background-color var(--t-fast) var(--ease-out),
      border-color var(--t-fast) var(--ease-out),
      color var(--t-fast) var(--ease-out);
  }

  .primary {
    background: var(--accent);
    color: var(--fg-inverse);
  }

  .primary:hover:not(:disabled) {
    background: var(--accent-hover);
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
    background: var(--danger);
    color: #fff;
  }

  :disabled {
    opacity: 0.4;
    cursor: not-allowed;
  }
</style>
