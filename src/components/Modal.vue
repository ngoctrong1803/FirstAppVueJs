<!-- eslint-disable vuejs-accessibility/click-events-have-key-events -->
<template>
  <!-- @click.self is one of 'click event modifiers' -->
  <div class="backdrop" @click.self="closeModal">
    <div class="modal" :class="{sale : theme === 'dynamic_class'}">
      <h1>Hello this is the modal 2</h1>
      {{ title_prop }}
      {{ text }}
      <p>data array</p>
      {{ data }}
      <slot></slot>
      <slot name="links"></slot>
    </div>
  </div>
</template>

<script>
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'Modal',
  props: ['title_prop', 'text', 'data', 'theme'],
  methods: {
    closeModal() {
      this.$emit('close');
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.modal{
  width: 400px;
  height: 300px;
  padding: 20px;
  margin: 100px auto;
  background: white;
  border-radius: 10px;
}
.backdrop{
  top: 0;
  position: fixed;
  background: rgba(227, 219, 219, 0.4);
  width: 100%;
  height: 100%;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
h1{
  color: aqua;
}
.modal.sale{
  color: red;
}
</style>
