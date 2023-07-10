<template>
  <h3>your score - <span>{{ score }}</span> s</h3>
  <h2>{{ text }} {{ rank }}</h2>
  <img :src="require('@/assets/lose.png')" alt="photo lose" v-if="x1">
  <img :src="require('@/assets/win.png')" alt="photo lose" v-if="x2">

</template>

<script>
export default {
    props:['score','audio2'],
    data(){
     return{
       rank:null,
       photo:'',
       text:null,
       x1:false,
       x2:false,
     }        
    
  },
    mounted(){
        if(this.score>0.5){
          this.x1=true
          this.text="you lose"
          this.rank="OLD MAN"
          this.audio2.play()
        }else if(this.score<0.5){
          this.x2=true
          this.text="you win"
          this.rank="NINJA BOY"
          this.audio2.play()
        }
    },
    unmounted(){
      this.audio2.pause()
    }

}
</script>

<style scoped>
*{font-family: 'Lemonada', cursive;}
h3{
color: rgb(59, 6, 22);
}
span{
    color: red;
}
h2{
    color: rebeccapurple;
}
img{
  width: 30%;
  height:30%;
}
</style>

