<template>
  
  <div class="container-fluide">
    <div class="mySlider d-flex align-items-center justify-content-center">
    <slider class=" d-flex justify-content-center align-items-center" @focus="handleFocus" :slides="slides"></slider>
    </div>

    <parameters class="hide" @addSlide="addSlide" @deleteSlide="deleteSlide" :slideIndex="slideIndex"></parameters>
  </div>
</template>

<script>
import slider from './components/slider.vue'
import parameters from './components/parameters.vue'

export default {
  data(){
    return {
      focusOn : null,
      count : 3,
      slideIndex : 1,
      slides : [
        {id : 0,img:require('./assets/img1.jpg')},
        {id : 1,img:require('./assets/img2.jpg')},
        {id : 2,img:require('./assets/img3.jpg')}
      ]
    }
  },
components: {
  slider,
  parameters
},
methods : {
  handleFocus(id){
    this.focusOn = id
    this.slides.map(slide => {
      if(slide.id === this.focusOn) {
        this.slideIndex = this.slides.indexOf(slide) + 1
        return
      }
    })
  },
  addSlide(){
    const newSlide = {
      id : this.count,
      img:require('./assets/img3.jpg'),
    }
    this.slides.push(newSlide)
    this.count++
  },
  deleteSlide(){
    this.slides = this.slides.filter(slide => slide.id != this.focusOn)

  }
}
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@300&display=swap');
*{
  margin : 0;
  padding : 0;
  box-sizing: border-box;
  font-family: 'Roboto', sans-serif;
}

.mySlider{
  width: calc(100% - 300px);
  padding : 2em;
  height : 100vh;
}
@media screen and (max-width:900px) {
  .hide{
    display : none;
  }
  .mySlider{
    width : 100%;
  }
}
</style>