<script>
  import { Role } from "./components/Role";
  import { roles, loves } from "../../../../data";

  const allItems = [...roles, ...loves];

  let selected;

  function handleHover(e) {
    selected = e.detail.id;
  }
</script>

<div class="wrapper">
  <div class="container">
    <h1>
      Hey there 👋
      <br />
      I'm Hugo Duarte
    </h1>
    <p>
      <span>I'm a</span>
      {#each roles as role, i}
        <Role
          item={role}
          index={i + 1}
          itemsLength={roles.length}
          on:hover={handleHover}
        />
      {/each}
      <span>&nbsp;from Aveiro, Portugal. I also enjoy</span>
      {#each loves as love, i}
        <Role
          item={love}
          index={i + 1}
          itemsLength={loves.length}
          on:hover={handleHover}
        />
      {/each}
      <span>.</span>
    </p>
    <div class="emojis-wrapper">
      {#each allItems as item}
        <span
          class="emoji {selected === item.id ? 'selected' : ''}"
          on:mouseover={() => (selected = item.id)}
          on:focus={() => (selected = item.id)}
          on:mouseout={() => (selected = null)}
          on:blur={() => (selected = null)}>{item.emoji}</span
        >
      {/each}
    </div>
  </div>
</div>

<style>
  .wrapper {
    background-color: honeydew;
    padding: 16px;
  }

  .container {
    text-align: center;
  }

  h1 {
    font-family: var(--font-code-bold);
  }

  .emojis-wrapper {
    font-size: 24px;
    line-height: 78px;
    display: flex;
    align-items: flex-end;
    justify-content: center;
  }

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
