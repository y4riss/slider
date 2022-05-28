<template>
 <div >
   <div id="carouselExampleDark" class="carousel carousel-dark slide" data-bs-ride="carousel">
  <div class="carousel-indicators" >
    <button ref="carouselButton" v-for="(slide,index) in slides" :key="slide.id" type="button" data-bs-target="#carouselExampleDark" :data-bs-slide-to="index" :class="{active:index===0}" :aria-current="index===0" ></button>
  </div>
  <div class="carousel-inner">
    <div ref="carouselInner" @click="handleFocus(slide.id)" :class="{active:index===0}"  class="carousel-item " data-bs-interval="10000"  v-for="(slide,index) in slides" :key="slide.id" >
      <img :src="slide.img" class="d-block w-100" alt="...">
      <div class="carousel-caption d-none d-md-block">
        <h5 contenteditable="true">{{index+1}}</h5>
        <p  contenteditable="true">Some representative placeholder content for the  slide.</p>
      </div>
    </div>

  </div>
  <button class="carousel-control-prev" type="button" data-bs-target="#carouselExampleDark" data-bs-slide="prev">
    <span class="carousel-control-prev-icon" aria-hidden="true"></span>
    <span class="visually-hidden">Previous</span>
  </button>
  <button class="carousel-control-next" type="button" data-bs-target="#carouselExampleDark" data-bs-slide="next">
    <span class="carousel-control-next-icon" aria-hidden="true"></span>
    <span class="visually-hidden">Next</span>
  </button>
</div>
      </div>
</template>

<script>

 
export default {
    props : ['slides'],

    data(){
      return{
          count : 3
      }
    },

  methods : {
    handleFocus(id){
      console.log(id)
      this.$emit('focus',id)
    }
  },
  watch:{
    slides : function(){
        if(this.slides.length < this.count){
      this.$refs.carouselInner[0].classList.add("active")
      this.$refs.carouselButton[0].classList.add("active")
      this.$refs.carouselButton[0].setAttribute("aria-current",true)
        }
        this.count = this.slides.length
    }
  }
}
</script>

<style scoped>
*{
  outline : none;
  color : white;
}
.slide{
  width : 80%;
}
img{
  width : 100%;
  height : 100%;
}
</style>