# numeric-keypad component

> numeric-keypad is a light component to add a numeric keypad to your vue project.
> No dependencies. Works with any framework (Vuetify, ecc.)

## Install

```
npm install @bit/swina.vue-components.components.numeric-keypad
```

### Demo

Demo [CodeSandbox](https://codesandbox.io/s/l2ovzz34m7)

### Usage

You need to define at least the onInput function in your template to get the key pressed from the keypad and use it in your data.

Props

(required):

```
onInput     : Function - to get the number pressed from the keypad
```

(optional)

```
onDelete    : Function - to delete the last number input from the keypad
onReset     : Function - to reset the number
show        : Boolean - Show the keypad
close       : String - Close button (empty no button is showed)
keypadClass : String - your specific class (see styling)
```

### Example

```
<template>
  <!-- display the sequence of key pressed from the keypad -->
  {{number}}
  <numerickeypad
    :onInput="onInput"
    :onDelete="onDelete"
    :onReset="onReset"
    :show="show"
    :close="Close"/>

</template>
<script>
import numerickeypad from '@bit/swina.vue-components.components.numeric-keypad'
export default {
  components:{
    numerickeypad
  },
  data:()=>({
    show: true, //display the keypad
    number: '', //your number
    maxLength: 6 //sequence max length from the keypad
  }),
  methods:{
    onInput(key) {
      this.number = ''
      this.number = (this.number + key).slice(0, this.maxLength);
    },
    onDelete() {
      this.number = this.number.slice(0, this.number.length - 1);
    },
    onReset(){
      this.number = ''
    },
  }
}
</script>
```

### Styling

By default the numeric-keypad as the following class

```
.keypad-class {
  color: #888;
  background: #fafafa;
  border:.004rem solid #eaeaea;
}
```

color : text color

background: keypad background

border: border color and size

You can change this values with the props keypadClass with your custom class.

## Build Setup

```bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report

# run unit tests
npm run unit

# run all tests
npm test
```

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).
