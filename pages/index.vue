<template>
  <section>
    <div id="container" />
  </section>
</template>

<script>
import Konva from 'konva'

export default {
  data() {
    return {
      isDragging: false
    }
  },
  mounted() {
    const stage = new Konva.Stage({
      container: 'container',
      width: 200,
      height: 200
    })
    console.log(stage)

    stage.on('mousedown', e => {
      this.isDragging = true
      const layer = this.addLayer()
      stage.add(layer)
      console.log(layer)
    })

    stage.on('mousemove', e => {
      if (this.isDragging) {
        console.log(e)
      }
    })

    stage.on('mouseup', e => {
      this.isDragging = false
      console.log(e)
    })
  },
  methods: {
    addLayer() {
      const layer = new Konva.Layer()

      const circle = new Konva.Circle({
        x: 10,
        y: 10,
        radius: 70,
        fill: 'red',
        stroke: 'black',
        strokeWidth: 4
      })
      console.log(circle.size())
      layer.add(circle)
      setTimeout(() => {
        layer.setAttr('x', 100)
        layer.draw()
      }, 1000)
      return layer
    }
  }
}
</script>

<style scoped>
</style>
