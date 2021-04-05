<template>
  <h1>{{ title }}</h1>
  <div v-if="showModal">
    <Modal :header="header" :text="text" :theme="theme" @close="toggleModal">
      <template v-slot:links>
        <a href="#">Sign up</a>
        <a href="#">Sign in</a>
      </template>

      <div>Slot values</div>
      <h1>Slot header 1</h1>
    </Modal>
  </div>
  <div v-if="showModelTwo">
    <Modal :header='headerTwo' @close='toggleSecondModal'>
      <template v-slot:links>
        <a href="#">a button</a>
        <a href="#">Another button</a>
      </template>
      <h1>This is the other modal</h1>
      <div>sub title and stuff</div>
    </Modal>
  </div>
  <br />
  <button @click.left="toggleSecondModal">Show another modal</button>
  <button @click.left="toggleModal">Open modal</button>
</template>

<script>
import Modal from "./components/Modal.vue";

export default {
  name: "App",
  components: { Modal },
  data() {
    return {
      title: "Practising Vue",
      header: "Sign up for the giveaway!",
      text: "Grab your item for half price",
      theme: "sale",
      showModal: false,
      showModelTwo: false
    };
  },
  methods: {
    toggleModal() {
      this.showModal = !this.showModal;
    },
    toggleSecondModal() {
      this.showModelTwo = !this.showModelTwo
    }
  },
  computed: {},
};
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
