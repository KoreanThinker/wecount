<style lang="postcss">
  .menu {
    background-color: white;
    display: flex;
    justify-content: center;
    align-items: center;
    width: 44px;
    height: 44px;
    box-sizing: border-box;
    border-radius: 10px;
    margin-bottom: 16px;
    cursor: pointer;
    border: 1.5px solid white;
    user-select: none;
  }

  .seleted-menu {
    border: 1.5px solid var(--green40);
  }

  .plus-menu {
    background-color: var(--gray20);
    background-position: center;
    transition: background 0.8s;
  }

  .plus-menu:hover {
    background: var(--gray30)
      radial-gradient(circle, transparent 1%, var(--gray30) 1%) center/15000%;
  }

  .plus-menu:active {
    background-color: var(--gray20);
    background-size: 100%;
    transition: background 0s;
  }
</style>

<script lang="ts">
  export let selectValue: string;
  export let style: string | undefined = undefined;
  export let isSelected = false;
  export let onSelect: (value: string) => void;
</script>

<div
  class="menu {$$props.class}"
  class:seleted-menu={isSelected}
  style={style}
  on:click={() => onSelect(selectValue)}
>
  <slot />
</div>
