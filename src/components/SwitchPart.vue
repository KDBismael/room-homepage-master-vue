<template>
  <div class="switch">
    <div v-on:click="previousImage" class="box">
      <svg width="14" height="24" xmlns="http://www.w3.org/2000/svg"><path d="M13 0L1 12l12 12" stroke="#FFF" fill="none" fill-rule="evenodd"/></svg>
    </div>
    <div v-on:click="nextImage" class="box">
      <svg width="14" height="24" xmlns="http://www.w3.org/2000/svg"><path d="M1 0l12 12L1 24" stroke="#FFF" fill="none" fill-rule="evenodd"/></svg>
    </div>
  </div>
</template>

<script>
export default {
  name:'switch',
  methods:{
    nextImage:function(){
      this.eventBus.emit('toNext','next')
    },
    previousImage:function(){
      this.eventBus.emit('toPrevious','previous')
    }
  },
}
</script>

<style src="../css/switch.css" scoped>

</style>