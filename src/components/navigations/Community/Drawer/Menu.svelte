<style lang="postcss">
  .sub-menu {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px 20px;
    cursor: pointer;
  }

  .selexted-name {
    font-size: 0.875rem;
    font-weight: 700;
    color: var(--text);
  }

  .unselected-name {
    font-size: 0.875rem;
    font-size: 400;
    color: var(--text);
  }

  .notification-counts {
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: var(--red10);
    min-width: 25px;
    height: 14px;
    border-radius: 1000px;
    font-size: 0.688rem;
    font-weight: bold;
    color: var(--red50);
    padding: 3px 1px;
  }
</style>

<script lang="ts">
  import type {MenuType} from '../../../../types';
  import {push} from 'svelte-spa-router';

  export let menu: MenuType;
  export let isSelected: boolean;
  export let selectMenu: (path: string) => void;

  const onClick = async (path: string) => {
    selectMenu(path);
    await push(menu.path);
  };
</script>

<div
  class="sub-menu"
  style="background-color: {isSelected
    ? 'var(--placeholder)'
    : 'var(--background)'}"
  on:click={() => onClick(menu.path)}
>
  <span class:selexted-name={isSelected} class:unselected-name={!isSelected}>
    {menu.name}
  </span>
  {#if menu.notificationCounts}
    <span class="notification-counts">
      +{menu.notificationCounts}
    </span>
  {/if}
</div>
