<!-- svelte-ignore css-unused-selector -->
<style lang="postcss">
  main {
    border: 1px solid var(--border);
    box-sizing: border-box;
    border-radius: 4px;
    padding: 11px 16px;

    display: flex;
    flex-direction: row;
    align-items: center;

    &:focus-within {
      border: 1px solid var(--input-focus);
    }

    input {
      flex: 1;
      color: var(--text);
      text-transform: none;
      font-size: var(--font-size, 14px);
      margin-left: 12px;
      margin-top: 4px;
      font-family: inherit;
      background-color: transparent;
      background: transparent;
      border: none;

      &:focus {
        outline: none;
      }

      &:-webkit-autofill {
        -webkit-box-shadow: 0 0 0 1000px var(--background-color) inset !important;
      }
    }
  }
</style>

<script lang="ts">
  import {createEventDispatcher} from 'svelte';

  export let placeholder = '';
  export let type = 'text';
  export let containerStyle = '';
  export let inputStyle = '';

  export let value = '';

  const dispatch = createEventDispatcher();

  // @ts-ignore
  const onChanged = (e) => {
    value = /^(number|range)$/.exec(type) ? +e.target.value : e.target.value;

    dispatch('changed', value);
  };
</script>

<main style={containerStyle}>
  <slot name="leftElement" />
  <input
    style={inputStyle}
    type={type}
    placeholder={placeholder}
    on:input={onChanged}
  />
  <slot name="rightElement" />
</main>
