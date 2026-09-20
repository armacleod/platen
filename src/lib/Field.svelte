<script>
  let {
    label,
    name,
    value = $bindable(''),
    type = 'text',
    error = '',
    hint = '',
    disabled = false
  } = $props();

  const id = $props.id();
</script>

<label class="quire-field">
  <span class="quire-kicker">{label}</span>
  <input {id} {name} {type} {disabled} bind:value aria-invalid={error ? 'true' : undefined} aria-describedby={hint || error ? id + '-msg' : undefined} />
  {#if error}
    <span class="msg err" id={id + '-msg'}>{error}</span>
  {:else if hint}
    <span class="msg" id={id + '-msg'}>{hint}</span>
  {/if}
</label>

<style>
  .quire-field {
    display: flex;
    flex-direction: column;
    gap: var(--s-02);
    min-width: 0;
  }

  input {
    appearance: none;
    height: var(--s-08);
    padding: 0 var(--s-04);
    border: var(--rule);
    border-radius: var(--r-1);
    background: var(--field-bg);
    color: var(--fg);
    font: var(--type-ui);
  }

  input:hover:not(:disabled) {
    border-color: var(--border-strong);
  }

  input:focus-visible {
    outline: 2px solid var(--focus);
    outline-offset: 2px;
  }

  input[aria-invalid='true'] {
    border-color: var(--danger);
    border-width: 2px;
  }

  .msg {
    font: var(--type-label);
    font-weight: 400;
    letter-spacing: 0.02em;
    color: var(--fg-subtle);
  }

  .err {
    color: var(--danger);
    font-weight: 600;
  }
</style>
