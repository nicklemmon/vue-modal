<template>
  <div class="overlay" v-bind:class="{ visible: isVisible }"></div>
</template>

<script>
  export default {
    name: 'Overlay',
    data() {
      return {
        isVisible: false
      }
    },
    methods: {
      show() {
        this.isVisible = true
      },
      hide() {
        this.isVisible = false
      }
    },
    created() {
      this.$root.$on( 'modal-open', this.show )

      this.$root.$on( 'modal-close', this.hide )
    }
  }
</script>

<style scoped>
  .overlay {
    position: absolute;
    z-index: -1;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.5);
    opacity: 0;
    transition: opacity var(--animDur) var(--animEasing);
  }

  .visible {
    opacity: 1;
    z-index: 5;
  }
</style>