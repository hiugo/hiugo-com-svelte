<script>
  import { Role } from "./components/Role";
  import { Emoji } from "./components/Emoji";
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
        <Emoji
          {item}
          isSelected={item.id === selected}
          on:hover={handleHover}
        />
      {/each}
    </div>
  </div>
</div>

<style>
  .wrapper {
    background-color: var(--black);
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
</style>
