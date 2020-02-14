<template lang="pug">
  canvas(id='canvas' ref='canvas'
    :width='size.w'
    :height='size.h'
    :style='canvasStyle'
    @mouseup.prevent='canvasClick'
    @mousedown.prevent='canvasClick'
    @touchstart.prevent='canvasClick'
    @touchend.passive='canvasClick'
    v-render-canvas='{links, nodes}'
    )
</template>
<script>
//import canvasStyles from '../lib/js/canvasStyles.js'
//import stylePicker from '../lib/js/stylePicker.js'
//import svgExport from '../lib/js/svgExport.js'

import ForceGraph3D from '3d-force-graph';



export default {
  name: 'threejs-renderer',
  props: [
    'size',
    'offset',
    'padding',
    'nodes',
    'selected',
    'linksSelected',
    'links',
    'nodeSize',
    'fontSize',
    'strLinks',
    'linkWidth',
    'nodeLabels',
    'labelOffset',
    'canvasStyles',
    'nodeSym',
    'noNodes'
  ],
  data () {
    return {
      hitCanvas: null,
      shapes: {},
      drag: null,
      stylesReady: false,
      CssStyles: true, // load style from css props
      // canvas styles
      styles: canvasStyles,
      sprites: {}
    }
  },
  computed: {
    /*
    nodeSvg () {
      return this.nodeSym
    },
    canvasStyle () {
      let left = this.padding.x + 'px'
      let top = this.padding.y + 'px'
      return { left, top }
    }
    */
  },
  directives: {
      /*
    renderCanvas (canvas, data, vnode) {
      let nodes = data.value.nodes
      let links = data.value.links
      vnode.context.draw(nodes, links, canvas)
    }
    */
  },
  created () {
      /*
    if (this.canvasStyles) {
      for (let o in this.canvasStyles) {
        this.styles[o] = this.canvasStyles[o]
      }
    }
    */
  },
  mounted () {
    let vm = this
    /*
    this.$nextTick(() => {
      vm.hitCanvas.width = vm.size.w
      vm.hitCanvas.height = vm.size.h
    })
    */
   const Graph = ForceGraph3D()
	(document.getElementById("3d-graph"));

  },
  watch: {
  },
  methods: {
  }
}
</script>
<style lang="stylus">
  canvas
    position absolute
    top 0
    left 0
</style>
