<script>
  import { createEventDispatcher } from "svelte";

  export let item;
  export let isSelected;

  const dispatch = createEventDispatcher();

  function handleHover(id) {
    dispatch("hover", { id });
  }
</script>

<span
  class="emoji {isSelected ? 'selected' : ''}"
  on:mouseover={() => handleHover(item.id)}
  on:focus={() => handleHover(item.id)}
  on:mouseout={() => handleHover(null)}
  on:blur={() => handleHover(null)}
>
  {item.emoji}
</span>

<style>
  .emoji {
    padding: 0 8px;
    transition: font-size 300ms;
    cursor: default;
    user-select: none;
  }

  .emoji.selected {
    font-size: 48px;
  }

  @media screen and (max-width: 360px) {
    .emoji {
      font-size: 16px;
      padding: 0 4px;
    }

    .emoji.selected {
      font-size: 32px;
    }
  }
</style>
