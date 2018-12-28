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
      count: 0
    }
  },
  mounted () {
    this.initWiv(this.$refs.wiv)
    window.requestAnimationFrame(this.animateLines)
  },
  methods: {
    animateLines () {
      let wivCurve = this.$refs.canvas
      let ctx = this.$refs.canvas.getContext('2d')
      let count = this.count
      ctx.beginPath()
      ctx.clearRect(0, 0, wivCurve.width, wivCurve.height)

      let x = this.height * 2 + this.thickness
      let y = this.height - Math.sin(((x - count) * this.tightness) * Math.PI / 180) * this.height + this.thickness

      // draw top
      for (x = this.height * 3; x <= wivCurve.width - (this.height * 3); x += 1) {
        y = this.height - Math.sin(((x - count) * this.tightness) * Math.PI / 180) * this.height + this.thickness
        ctx.lineTo(x, y)
      }

      // draw right
      for (; y <= wivCurve.height - (this.height * 3); y += 1) {
        x = (wivCurve.width - this.height * 3) + this.height - Math.cos(((y - count) * this.tightness) * Math.PI / 180) * this.height + this.thickness
        ctx.lineTo(x, y)
      }

      // draw bottom
      for (; x >= (this.height * 3); x -= 1) {
        y = (wivCurve.height - this.height * 3) + this.height - Math.sin(((x - count) * this.tightness) * Math.PI / 180) * this.height + this.thickness
        ctx.lineTo(x, y)
      }

      // draw left
      for (; y >= (this.height * 2) + this.thickness; y -= 1) {
        x = this.height - Math.cos(((y - count) * this.tightness) * Math.PI / 180) * this.height + this.thickness
        ctx.lineTo(x, y)
      }

      // draw top
      for (; x <= wivCurve.width - (this.height * 3); x += 1) {
        y = this.height - Math.sin(((x - count) * this.tightness) * Math.PI / 180) * this.height + this.thickness
        ctx.lineTo(x, y)
      }

      // pull color from dataset
      ctx.strokeStyle = this.color
      ctx.lineWidth = this.thickness

      ctx.stroke()

      // current frame is tracked on per wiv basis. This is to help with speed calculations
      if (count > 100000) {
        count = 0
      }

      count = (count || 0) + this.speed
      this.count = count

      // reanimate
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
