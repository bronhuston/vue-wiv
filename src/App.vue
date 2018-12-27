<template>
  <div id="app">
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
<style>
</style>
