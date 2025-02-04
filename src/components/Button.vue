<template>
  <div :class="buttonClass" @click='clickButton'>
    {{text}}
  </div>
</template>

<script>
export default {
  props: ['text', 'buttonClass'],
  emits: ['click-button'],
  methods: {
    clickButton() {
      this.$emit('click-button', this.text)
    }
  }
}
</script>

<style>
  .button {
    border: 1px solid black;
  }
  .main-button {
    font-weight: bold;
    width: 300px;
    padding: 10px;
    border: 2px solid black;
    font-size: 17px;
    border-radius: 10px;
  }
  .main-button:hover {
    background-color: #5a947a;
    color: #cce2cc;
    border: 2px solid #cce2cc;
  }
  .rounded-button {
    background-color: #cce2cc;
    color: #5a947a;
    border: 2px solid #5a947a;
    border-radius: 20px;
    font-size: 15px;
    font-weight: 700;
    padding: 2px;
    width: 150px;
    margin: 1px;
  }
  .rounded-button:hover {
    background-color: #daebda;
  }
</style>
