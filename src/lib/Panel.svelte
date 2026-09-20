<script>
  let { kicker = '', title = '', atmosphere = false, children } = $props();
</script>

<section class={['quire-panel', atmosphere && 'atmosphere']}>
  {#if kicker}
    <p class="quire-kicker">{kicker}</p>
  {/if}
  {#if title}
    <h2>{title}</h2>
  {/if}
  {@render children?.()}
</section>

<style>
  .quire-panel {
    background: var(--bg);
    border: var(--rule);
    border-radius: var(--r-0);
    padding: var(--s-06);
  }

  .atmosphere {
    background-image: var(--grad-atmosphere);
  }

  h2 {
    font: var(--type-heading);
    margin: var(--s-02) 0 var(--s-05);
  }
</style>
