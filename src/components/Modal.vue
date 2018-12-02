<template>
  <div class="modal" v-bind:class="{ open: isOpen }" :aria-hidden="isOpen ? false : true" role="dialog">
    <button class="modalClose" aria-label="Close" v-on:click="close" tabindex="0">
      <Icon class="modalCloseIcon" name="times"></Icon>
    </button>

    <div v-if="heading" class="modalHeader">
      <h3 class="modalHeading" tabindex="-1">{{ heading }}</h3> <!-- negative tabindex for .focus() -->
    </div>

    <div class="modalContent">
      <slot></slot>
    </div>
  </div>
</template>

<script>
  import Icon from 'vue-awesome/components/Icon'
  import 'vue-awesome/icons/times'

  export default {
    name: 'Modal',
    components: {
      Icon
    },
    data() {
      return {
        isOpen: false
      }
    },
    props: {
      heading: {
        type: String,
        default: ''
      }
    },
    methods: {
      open() {
        this.isOpen = true
      },
      close() {
        this.isOpen = false

        this.$root.$emit( 'modal-close' )
      }
    },
    mounted() {
      this.$root.$on( 'modal-open', this.open )
    }
  }
</script>

<style scoped>
  .modal {
    position: fixed;
    z-index: 10;
    top: 50%;
    left: 50%;
    width: 90%;
    max-width: 800px;
    padding: var(--spacingLg);
    background: var(--background);
    border-radius: var(--borderRadius);
    box-shadow: 0 var(--spacingMd) var(--spacingLg) rgba(0, 0, 0, 0.1);
    transform: scale(0) translate(-50%, -50%); /* see: http://lynn.io/2014/02/22/modalin/ */
  }

  .modal.open {
    transform: scale(1) translate(-50%, -50%);
  }

  .modalClose {
    border: 0;
    outline: 0;
    padding: 0;
    background: transparent;
    position: absolute;
    top: var(--spacingLg);
    right: var(--spacingLg);
  }

  .modalClose:focus {
    outline: 1px dashed currentColor;
  }

  .modalCloseIcon {
    color: var(--accent);
    width: var(--fontSizeLg);
    height: var(--fontSizeLg);
    transition: transform var(--animDur) var(--animEasing);
  }

  .modalCloseIcon:hover {
    transform: scale(1.25);
  }
</style>