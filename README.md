# vue-wiv

Vue component for wiggly divs ([wiv.js](https://github.com/jjkaufman/wiv.js))

Initialized with the [Vue CLI](https://cli.vuejs.org/).

## Install

```
npm install --save vue-wiv

```

## Usage
See [App.vue](./src/App.vue) for an example implementation

```
<template>
  <div>
    <Wiv>
      <span>Default Wiv</span>
    </Wiv>
    <Wiv
      color="#4B0082"
      :height="8"
      :speed=".15"
      :thickness="2"
      :tightness="6"
    >
      <div>Slow and Wiggly</div>
    </Wiv>
    <Wiv>
      <Wiv>Wiv-ception</Wiv>
    </Wiv>
  </div>
</template>
<script>
import Wiv from 'vue-wiv'
export default {
  name: 'MyComponent',
  components: { Wiv }
}
</script>
```
