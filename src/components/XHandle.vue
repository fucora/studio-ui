<template>
  <div class="x-handle" 
    @mousedown="mouseDown" 
  ></div>
</template>

<script>
export default {
  name: 'XHandle',
  data () {
    return {
      //dragging : false,
      lastX:''
    }
  },

  created () {
    document.addEventListener('mouseup', this.mouseUp)
  },

  destroyed() {
    document.removeEventListener('mouseup', this.mouseUp)
  },


  methods: {
    mouseDown(event){
      document.addEventListener('mousemove', this.mouseMove)
      this.lastX = event.screenX
    },
    mouseMove(event){
      this.$emit('widthChange', event.screenX - this.lastX)
      this.lastX = event.screenX
    },
    mouseUp(event){
      this.lastX = ''
      document.removeEventListener('mousemove', this.mouseMove)
    },
  },
}
</script>

<style>
</style>