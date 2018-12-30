# vue-wiv &middot; [![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](./LICENSE) [![npm version](https://img.shields.io/npm/v/vue-wiv.svg?style=flat)](https://www.npmjs.com/package/vue-wiv) [![JavaScript Style Guide](https://img.shields.io/badge/code_style-standard-brightgreen.svg)](https://standardjs.com)

Vue component for wiggly divs ([wiv.js](https://github.com/jjkaufman/wiv.js))

Initialized with the [Vue CLI](https://cli.vuejs.org/).
## Install

```
npm install --save vue-wiv

```

## Example

![Example](https://media.giphy.com/media/fdA9EkzWgHzvvpqxdM/giphy.gif)

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
