<template>
  <div class="app" id="app">
    <Modal heading="This is a modal heading.">
      This is the modal content.
    </Modal>

    <Overlay/>

    <div id="content"> <!-- hidden from screen readers when a modal is open -->
      <header id="header"></header>

      <main id="content">
        <ModalBtn
          btnType="primary" 
          btnContent="Open Modal" 
        />
      </main>

      <footer id="footer"></footer>
    </div>
  </div>
</template>

<script>
  import Modal from './components/Modal.vue'
  import Overlay from './components/Overlay.vue'
  import ModalBtn from './components/ModalBtn.vue'

  export default {
    name: 'App',
    data() {
      return {
        keyCode: ''
      }
    },
    components: {
      Modal,
      Overlay,
      ModalBtn
    }
  }
</script>

<style>
  .app,
  #content {
    height: 100%;
    width: 100%;
  }

  #content {
    position: relative; /* to allow use of z-index */
    z-index: 0;
    display: flex;
    align-items: center;
    justify-content: center;
  }
</style>
