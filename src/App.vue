<template>
  <!-- <teleport to="#modals">
    <modal v-if="showModal === true" @close="toggleModal">
      <template v-slot:links> 
        <a href="#">sign up now</a>
        <a href="#">more info</a>
      </template>
      <h1>Ninja Giveaway!</h1>
      <p>Grab your ninja swag for hal9uf price!</p>
    </modal>
  </teleport>
  
  <modal v-if="showModalTwo == true" @close="toggleModalTwo">
    <template v-slot:data> 
      <h1>Sign up to the newsletter</h1>
      <p>For updates and promo codes</p>
    </template>
  </modal>
  <div class="showModalbtn">
    <button @click.alt="toggleModal">Show Modal (alt)</button>
    <button @click="toggleModalTwo">Show Modal 2</button>
  </div> -->
  <h1>Ninja Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying == true">play</button>
  <block v-if="isPlaying == true" :delay="delay" @end="endGame"></block>
  <result :score="score" v-if="showResult == true"></result>
</template>

<script>
import Modal from './components/Modal';
import Block from "./components/Block.vue";
import Result from "./components/Result.vue";

export default {
  name: 'App',
  components: {
    Modal,
    Block,
    Result
  },
  data() {
    return {
      heading: 'Sign up for the Givaway!',
      text: 'Grab your ninja swag for half price!',
      showModal: false,
      showModalTwo: false,
      delay: null,
      isPlaying: false,
      score: null,
      showResult: false
    }
  },
  methods: {
    toggleModal() {
      this.showModal = !this.showModal;
    },
    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo
    },
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      this.showResult = false;
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResult = true;
    }
  }
}
</script>

<style>
  #app {
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #444;
    margin-top: 60px;
  }
  .showModalbtn {
    text-align: center;
    width: 400px;
    padding: 20px;
    margin: 200px auto;
  }
  button {
    background: #0faf87;
    color: white;
    border: none;
    padding: 8px 16px;
    border-radius: 4px;
    font-size: 16px;
    letter-spacing: 1px;
    cursor: pointer;
    margin: 10px;
  }
  button[disabled] {
    opacity: 0.2;
    cursor: not-allowed;
  }
</style>
