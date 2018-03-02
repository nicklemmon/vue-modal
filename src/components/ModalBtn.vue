<template>
  <Btn
    :type="btnType"
    :content="btnContent"
    :clickHandler="openModal"
    screenReaderPostContent="Opens a dialog"
  />
</template>

<script>
  import Btn from './Btn.vue'

  export default {
    name: 'ModalBtn',
    components: {
      Btn
    },
    props: [
      'btnType',
      'btnContent'
    ],
    methods: {
      openModal() {
        console.log( 'open modal' )
        this.$root.$emit( 'modal-open' )
      }
    }
  }
</script>

<style scoped>
</style>