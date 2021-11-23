<script>
  import { createEventDispatcher } from "svelte";

  export let item;
  export let index;
  export let itemsLength;

  const dispatch = createEventDispatcher();

  const isLast = index === itemsLength;
  const isSecondLast = index === itemsLength - 1;

  function handleHover(id) {
    dispatch("hover", { id });
  }
</script>

<span
  class="skill"
  on:mouseover={() => handleHover(item.id)}
  on:focus={() => handleHover(item.id)}
  on:mouseout={() => handleHover(null)}
  on:blur={() => handleHover(null)}
>
  {item.title}
</span>
{#if isSecondLast}
  <span>and&nbsp;</span>
{:else}
  <span class="no-spacing">{isLast ? "" : ", "}</span>
{/if}

<style>
  .skill {
    cursor: pointer;
    text-decoration: underline;
    white-space: nowrap;
  }

  .no-spacing {
    margin-left: -10px;
  }
</style>
