<script>
  let { strong = false, label = '' } = $props();
</script>

<div class={['quire-rule', strong && 'strong']}>
  {#if label}
    <span>{label}</span>
  {/if}
</div>

<style>
  .quire-rule {
    display: flex;
    align-items: center;
    gap: var(--s-04);
    border: 0;
    border-top: var(--rule);
    height: 0;
    margin: var(--s-07) 0;
  }

  .strong {
    border-top: var(--rule-strong);
  }

  span {
    font: var(--type-label);
    letter-spacing: 0.08em;
    text-transform: uppercase;
    color: var(--fg-subtle);
    background: var(--bg);
    padding-right: var(--s-03);
    transform: translateY(-50%);
  }
</style>
