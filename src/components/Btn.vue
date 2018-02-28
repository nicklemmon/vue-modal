<template>
  <button class="btn" :class="type" v-on:click="clickHandler">
    {{ content }}
  </button>
</template>

<script>
  export default {
    name: 'Btn',
    props: [
      'type',
      'content',
      'clickHandler'
    ]
  }
</script>

<style scoped>
  .btn {
    border-radius: 5px;
    background-color: var(--pink);
    font-size: var(--fontSizeSm);
    cursor: pointer;
    outline: none;
    border: 2px solid transparent;
    padding: var(--spacingSm) var(--spacingMd);
    transition: transform var(--animDur) var(--animEasing);
  }

  .btn:hover {
    transform: scale(1.025);
  }

  .primary {
    color: white;
    background-color: var(--highlight);
  }

  .secondary {
    color: var(--highlight);
    background-color: white;
    border-color: var(--highlight);
  }

  .tertiary {
    color: var(--highlight);
    background-color: white;
  }
</style>