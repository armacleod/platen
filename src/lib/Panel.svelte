<script>
  let { kicker = '', title = '', ground = 'sheet', children } = $props();
</script>

<section class={['platen-panel', ground]}>
  {#if kicker}
    <p class="platen-kicker">{kicker}</p>
  {/if}
  {#if title}
    <h2>{title}</h2>
  {/if}
  {@render children?.()}
</section>

<style>
  .platen-panel {
    background: var(--bg);
    border: var(--rule);
    border-radius: var(--r-0);
    padding: var(--s-06);
  }

  .platen-panel.void {
    background: var(--q-void);
    color: #f0eee7;
    border-color: #2c333c;
    background-image: var(--grad-void-bloom);
  }

  .platen-panel.fountain {
    background-image: var(--grad-fountain);
  }

  h2 {
    font: var(--type-heading);
    margin: var(--s-02) 0 var(--s-05);
  }
</style>
