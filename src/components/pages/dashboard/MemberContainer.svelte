<style lang="postcss">
  .wrap {
    width: 50px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    cursor: pointer;

    @media (--mobile) {
      width: 50%;
    }
  }
  .wrap:not(:last-child) {
    @media (--mobile) {
      margin-bottom: 20px;
    }
  }
  .name {
    width: 50px;
    margin-top: 6px;
    text-align: center;
    text-overflow: ellipsis;
    overflow: hidden;
    white-space: nowrap;

    @media (--mobile) {
      width: 100%;
    }
  }
</style>

<script lang="ts">
  export let name: string;
</script>

<div class="wrap">
  <slot />
  <div class="name">{name}</div>
</div>
