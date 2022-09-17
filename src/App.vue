<template>
  <modal :heading="heading" :text="text" theme="sale" v-if="showModal === true" @close="toggleModal"></modal>
  <div class="showModalbtn">
    <button @click.alt="toggleModal">Show Modal (alt)</button>
  </div>
</template>

<script>
import Modal from './components/Modal'

export default {
  name: 'App',
  components: {
    Modal
  },
  data() {
    return {
      heading: 'Sign up for the Givaway!',
      text: 'Grab your ninja swag for half price!',
      showModal: false
    }
  },
  methods: {
    toggleModal() {
      this.showModal = !this.showModal;
    }
  }
}
</script>

<style scoped>
  .showModalbtn {
    text-align: center;
    width: 400px;
    padding: 20px;
    margin: 200px auto;
  }
</style>
