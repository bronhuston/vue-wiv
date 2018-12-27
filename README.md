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
  <div id="app">
    <Wiv>
      <span>Default Wiv</span>
    </Wiv>
    <Wiv
      color="#FFFF00"
      :height="8"
      :speed=".15"
      :thickness="2"
      :tightness="6"
    >
      Rough
    </Wiv>
  </div>
</template>
<script>
import Wiv from './components/Wiv.vue'
export default {
  name: 'App',
  components: { Wiv }
}
</script>
```
