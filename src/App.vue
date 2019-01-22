<template>
  <div id="app">
    Number is : {{ number }}<br />
    <a href="#" @click="showKeypad = !showKeypad;"><h4>Toggle Keypad</h4></a>
    <numericpad
      :onInput="onInput"
      :onDelete="onDelete"
      :onReset="onReset"
      :show="showKeypad"
    />
  </div>
</template>
<script>
import numericpad from "@/components/numeric-keypad.vue";

export default {
  name: "app-numeric-keypad",
  components: {
    numericpad
  },
  data: () => ({
    number: "",
    maxLength: 6,
    showKeypad: true
  }),
  methods: {
    onInput(key) {
      this.number = (this.number + key).slice(0, this.maxLength);
    },
    onDelete() {
      this.number = this.number.slice(0, this.number.length - 1);
    },
    onReset() {
      this.number = "";
    }
  }
};
</script>
<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin-top: 20px;
}
</style>
