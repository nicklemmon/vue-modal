<template>
  <button class="btn" :class="type" v-on:click="clickHandler" tabindex="0">
    {{ content }}

    <span class="u-sr-only" v-if="screenReaderPostContent">
      {{ screenReaderPostContent }}
    </span>
  </button>
</template>

<script>
  export default {
    name: 'Btn',
    props: [
      'type',
      'content',
      'clickHandler',
      'screenReaderPostContent'
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

  .btn:focus {
    outline: 1px dashed currentColor;
    outline-offset: -3px;
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