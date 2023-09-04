<template>
  <h1>{{ title }}</h1>
  <p>Welcome ...</p>
  <div v-if="showModal">
    <Modal :header='header' :text='text' theme="danger" @close="toggleModal"/>
  </div>

  <div v-if="showSlotModal">
    <SlotModal @close="toggleSlotModal">
      <h1>Slot Title</h1>
      <p>Slot Text !!</p>
      <template v-slot:links>
        <a href="#">Click me : i'm a named slot :)</a><br>
        <a href="#">Click me : i'm one too :)</a>
      </template>
    </SlotModal>
  </div>


  <div v-if="showSlotModal2">
    <SlotModal @close="toggleSlotModal2" theme="danger">
      <h1>Slot Title 2</h1>
      <p>Slot Text 2 !!</p>
      <p>More text !!</p>
      <template v-slot:links>
        <a href="#">Click me 2 : i'm a named slot :)</a><br>
        <a href="#">Click me 2 : i'm one too :)</a>
      </template>
    </SlotModal>
  </div>

  <teleport to=".teleportModals" v-if="showTeleportModal">
    <Modal :header='header' text='Teleport Modal' theme="danger" @close="toggleTeleportModal"/>
  </teleport>


  <button @click="toggleModal">open modal</button>
  <button @click="toggleSlotModal">open slot modal</button>
  <button @click="toggleSlotModal2">open slot modal 2</button>
  <button @click="toggleTeleportModal">open teleport modal</button>
</template>

<script>
import Modal from './components/Modal.vue'
import SlotModal from './components/SlotModal.vue'

export default {
  name: 'App',
  components: { Modal, SlotModal },
  data() {
    return {
      title: 'My First Vue App :)',
      header: 'Modal\'s Title !!',
      text: 'Modal\'s text !!! \\o/',
      showModal: false,
      showSlotModal: false,
      showSlotModal2: false,
      showTeleportModal: false,
    }
  },
  methods: {
    toggleModal() {
      this.showModal = !this.showModal
    },
    toggleSlotModal() {
      this.showSlotModal = !this.showSlotModal
    },
     toggleSlotModal2() {
      this.showSlotModal2 = !this.showSlotModal2
    },
    toggleTeleportModal() {
      this.showTeleportModal = !this.showTeleportModal
    },
  }
  
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1 {
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>
