<!-- eslint-disable vue/valid-v-bind -->
<!-- eslint-disable max-len -->
<!-- eslint-disable vuejs-accessibility/form-control-has-label -->
<template>
    <h1>{{ title }}</h1>
    <input type="text" ref="name">
    <button @click="handleClick">click me!</button>
    <div v-if="showModal">
        <Modal :title_prop="title_prop"
              text="this property text is a prop"
              v-bind:data="['dataString', 4, {'keya':'valuea'}]"
              theme="dynamic_class"
              @close="toggleModal">
              <template v-slot:links>
                <a href="#">link to website</a>
              </template>
              <div>
                <h1>this is learning about slots</h1>
              </div>
        </Modal>
    </div>

    <Teleport to=".modals" v-if="showModal2">
        <Modal :title_prop="title_prop"
              text="this property text is a prop"
              v-bind:data="['dataString', 4, {'keya':'valuea'}]"
              theme="dynamic_class"
              @close="toggleModal">
              <template v-slot:links>
                <a href="#">link to website</a>
              </template>
              <div>
                <h1>this is learning about slots</h1>
              </div>
        </Modal>
    </Teleport>
    <button @click="toggleModal">Show Modal</button>
    <button @click="toggleModalTwo">Show Modal 2</button>
</template>

<script>
import Modal from './components/Modal.vue';

export default {
  name: 'App',
  components: {
    Modal,
  },
  data() {
    return {
      title: 'My First We',
      // prop
      title_prop: 'this property is a prop and it will pass into modal',
      showModal: false,
      showModal2: false,
    };
  },
  methods: {
    handleClick() {
      console.log(this.$refs.name);
      this.$refs.name.classList.add('active');
      this.$refs.name.focus();
    },
    toggleModal() {
      this.showModal = !this.showModal;
    },
    toggleModalTwo() {
      this.showModal2 = !this.showModal2;
    },
  },
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
</style>
