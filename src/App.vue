<template>
  <div class="mainContent">
    <div class="top" v-if="mobile">
      <Header :mobile="mobile"></Header>
      <description :mobile="mobile"></description>
    </div>
    <Header v-if="!mobile" :mobile="mobile"></Header>
    <description v-if="!mobile" :mobile="mobile"></description>
    <about class="about"></about>
  </div>
</template>

<script>
import about from './components/about.vue'
import Header from './components/header.vue'
import description from './components/description.vue'

export default {
  name: 'App',
  data(){
    return{
      mobile:false,
      width:null,
    }
  },created(){
    this.checkMobile();
    window.addEventListener('resize',()=>{
      this.checkMobile();
    })
    console.log(this.mobile)
  },
  components:{
    about,
    Header,
    description,
  },
  methods:{
    checkMobile:function() {
      this.width=window.innerWidth
      if(this.width<=750){
        this.mobile=true
      }
      else{
        this.mobile=false
      }
    }
  },
}
</script>

<style>
body,html{
  width: 100%;
  height: 100%;
}
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app{
  width: 100%;
  height: 100%;
}
.mainContent{
  display: grid;
  grid-template-columns: 1.5fr 1fr;
  width: 100%;
  height: 100%;
}
@media (max-width:750px){
  .mainContent{
    grid-template-columns:1fr;
    grid-template-rows: .9fr 1fr;
  }
  .top{
    width: 100%;
    height: 100%;
    display: grid;
    grid-template-columns: 1fr;
    grid-template-rows: auto 1fr;
  }
}
</style>
