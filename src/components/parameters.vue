<template>
  
  <div class="parameters pt-2">
     <p class="parameter-title">Slide Options</p>
     <p class="sub-parameter-title">slide number : {{slideIndex}}</p>
    <div class="f" >
      <p>Add / Delete slide</p>
<svg xmlns="http://www.w3.org/2000/svg"  @click="addSlide" width="24" height="24" style="fill: white;transform: ;msFilter:;"><path d="M15 2.013H9V9H2v6h7v6.987h6V15h7V9h-7z"></path></svg>
<svg xmlns="http://www.w3.org/2000/svg"  @click="deleteSlide" width="24" height="24" style="fill: white;transform: ;msFilter:;"><path d="M5 20a2 2 0 0 0 2 2h10a2 2 0 0 0 2-2V8h2V6h-4V4a2 2 0 0 0-2-2H9a2 2 0 0 0-2 2v2H3v2h2zM9 4h6v2H9zM8 8h9v12H7V8z"></path><path d="M9 10h2v8H9zm4 0h2v8h-2z"></path></svg>    
    </div>

    
  </div>
</template>

<script>
export default {
  props : ['slideIndex'],
  methods : {
    addSlide(){
      this.$emit('addSlide')
    },
    deleteSlide(){
      this.$emit('deleteSlide')
    }
  }
}
</script>

<style scoped>
.parameters{
    background : #282828;
    height : 100vh;
    width : 300px;
    position : fixed;
    top : 0;
    right : 0;

}
button{
  outline : none;
  border : none;
  padding : .5em 1.2em;
  border-radius : 4px;
  border : 1px solid black;
  color: white;
    background: #414141;
}
.f{
  display : flex;
  justify-content: space-around;
}
p{
  color : white;
}
.parameter-title{
  padding : .2em 0;
  background : #414141;
  text-align: center;
  font-weight: bolder;
  margin-top : 2em;
  margin-bottom : 0;
}
svg{
  cursor : pointer;  
}
.sub-parameter-title{
  padding : .1em 0;
  background : #414141;
  border: 2px solid white;
  padding-left: 10px;
}
</style>