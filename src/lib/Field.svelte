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
  <input {id} {name} {type} {disabled} bind:value aria-invalid={error ? 'true' : undefined} />
  {#if error}
    <span class="msg err">{error}</span>
  {:else if hint}
    <span class="msg">{hint}</span>
  {/if}
</label>

<style>
  .quire-field {
    display: flex;
    flex-direction: column;
    gap: var(--s-02);
  }

  input {
    appearance: none;
    height: var(--s-08);
    padding: 0 var(--s-04);
    border: var(--rule);
    border-radius: var(--r-1);
    background: var(--bg-subtle);
    color: var(--fg);
    font: var(--type-ui);
  }

  input:focus-visible {
    outline: 2px solid var(--focus);
    outline-offset: 2px;
  }

  input[aria-invalid='true'] {
    border-color: var(--danger);
  }

  .msg {
    font: var(--type-label);
    letter-spacing: 0.02em;
    color: var(--fg-subtle);
  }

  .err {
    color: var(--danger);
  }
</style>
