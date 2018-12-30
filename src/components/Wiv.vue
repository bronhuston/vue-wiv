<template>
  <div
    class="wiv"
    ref="wiv"
    :style="wivContainerStyles"
  >
    <canvas
      ref="canvas"
      :style="canvasStyles"
    />
    <div
      class="wiv-content"
      :style="{padding: height * 4 + 'px'}"
    >
      <slot />
    </div>
  </div>
</template>

<script>
import { wiv } from 'wiv.js'
export default {
  name: 'Wiv',
  props: {
    color: { type: String, required: false, default: '#7EFFDF' },
    height: { type: Number, required: false, default: 10 },
    speed: { type: Number, required: false, default: 1 },
    tightness: { type: Number, required: false, default: 8 },
    thickness: { type: Number, required: false, default: 2 }
  },
  data () {
    return {
      count: 0,
      increment: 1,
      wiv: wiv()
    }
  },
  mounted () {
    this.initWiv(this.$refs.wiv)
    window.requestAnimationFrame(this.animateLines)
  },
  methods: {
    animateLines () {
      if (!this.$refs) {
        return
      }
      let wivCurve = this.$refs.canvas

      this.count = this.wiv.drawLines(wivCurve, this.speed, this.height, this.tightness, this.thickness, this.increment, this.count, this.color)

      window.requestAnimationFrame(this.animateLines)
    },
    initWiv (wiv) {
      this.$refs.canvas.className = 'wiv-curves'
      this.$refs.canvas.width = wiv.offsetWidth
      this.$refs.canvas.height = wiv.offsetHeight
    }
  },
  computed: {
    canvasStyles () {
      return {
        zIndex: 16,
        position: 'absolute',
        pointerEvents: 'none'
      }
    },
    wivContainerStyles () {
      return {
        display: 'inline-block',
        borderRadius: this.height + 'px'
      }
    }
  }
}
</script>
<style>
</style>
