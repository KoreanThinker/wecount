<style lang="postcss">
  .tab-navigation {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .tab-layout {
    display: flex;
    width: 100%;
    justify-content: space-between;
    border-bottom: 1px solid var(--gray40);
  }

  .tab {
    cursor: pointer;
    font-size: 0.875rem;
    padding: 3px 5px;
  }

  .tab:not(:last-child) {
    margin-right: 12px;
  }

  .active-tab {
    border-bottom: 2px solid var(--gray100);
    font-weight: bold;
  }
</style>

<script lang="ts">
  import type {TabNavigationType} from '../../types';

  export let tabs: TabNavigationType[];
  export let tabNavigationStyle: string | undefined = undefined;
  export let tabStyle: string | undefined = undefined;

  let activeIndex = 0;

  const onTab = (index: number) => (activeIndex = index);
</script>

<div class="tab-navigation" style={tabNavigationStyle}>
  <div class="tab-layout">
    {#each tabs as tab, index}
      <div
        class="tab"
        style={tabStyle}
        on:click={() => onTab(index)}
        class:active-tab={index == activeIndex}
      >
        {tab.name}
      </div>
    {/each}
  </div>
  <svelte:component
    this={tabs[activeIndex].component.component}
    {...tabs[activeIndex].component.props}
  />
</div>
