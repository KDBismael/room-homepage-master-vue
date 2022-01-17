<template>
  <div class="description">
    <h1 v-text="Default.title"></h1>
    <p v-text="Default.info"></p>
    <div class="shop">
      <p>SHOP NOW</p>
    </div>
    <Switch v-if="!mobile"></Switch>
  </div>
</template>

<script>
import Switch from '../components/SwitchPart.vue'
export default {
    name:'description',
    components:{
      Switch
    },props:{
      mobile:Boolean,
    },
    created(){
      this.listenNext();
      this.listenPrevious();
    },
    data(){
      return{
        Default:{
          title:'Discover innovative ways to decorate',
          info:"We provide unmatched quality,comfort, and style for property owners across the country.Our experts combine form and function in bringing your vision to life. Create a room in your own style with our collection and make your property a reflection of you and what you love.", 
        },
        discover:{
          title:'Discover innovative ways to decorate',
          info:"We provide unmatched quality,comfort, and style for property owners across the country.Our experts combine form and function in bringing your vision to life. Create a room in your own style with our collection and make your property a reflection of you and what you love.", 
        },
        available:{
          title:'We are available all across the globe',
          info:"With stores all over the world, it's easy for you to find furniture for your home or place of business.Locally, we’re in most major cities throughout the country. Find the branch nearest you using our store locator. Any questions? Don't hesitate to contact us today.", 
        },
        manufactured:{
          title:'Manufactured with the best materials',
          info:"Our modern furniture store provide a high level of quality. Our company has invested in advanced technology to ensure that every product is made as perfect and as consistent as possible. With three decades of experience in this industry, we understand what customers want for their home and office.", 
        }
      }
    },
    methods:{
      listenNext:function(){
            this.eventBus.on('toNext',(data)=>{
                this.change=data
                this.nextDescription()
            })
        },
      listenPrevious:function(){
            this.eventBus.on('toPrevious',(data)=>{
                this.change=data
                this.previousDescription()
            })
        },
      nextDescription:function() {
        if (this.Default.title==this.discover.title) {
          this.Default.title=this.available.title
          this.Default.info=this.available.info
        }
        else if(this.Default.title==this.available.title){
          this.Default.title=this.manufactured.title
          this.Default.info=this.manufactured.info
        }
        else if(this.Default.title==this.manufactured.title){
          this.Default.title=this.discover.title
          this.Default.info=this.discover.info
        }
        else{
          this.Default.title=this.discover.title
          this.Default.info=this.discover.info
        }
      },
      previousDescription:function() {
        if (this.Default.title==this.discover.title) {
          this.Default.title=this.manufactured.title
          this.Default.info=this.manufactured.info
        }
        else if(this.Default.title==this.available.title){
          this.Default.title=this.discover.title
          this.Default.info=this.discover.info
        }
        else if(this.Default.title==this.manufactured.title){
          this.Default.title=this.available.title
          this.Default.info=this.available.info
        }
        else{
          this.Default.title=this.discover.title
          this.Default.info=this.discover.info
        }
      }
    }
}
</script>

<style src="../css/description.css" scoped>
</style>