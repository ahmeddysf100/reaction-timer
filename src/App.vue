<template>
  <h1>Ninja reaction timer</h1>
  <button class="play-btn" @click="start" :disabled="isPlaying">blay</button>  <!--:disabled="isPlaying" ديسايبلد هاي ميزه بالاج تي ام ال معناه تغي دكمه لمن قيمته ترو-->
  <br>
  <block v-if="isPlaying" :delay="delay" :photo="photo" @end="endGame">
  </block>
  <results v-if="showResult" :score="score" :audio2="audio2">
  </results>
</template>

<script>
import block from './components/Block.vue'
import results from './components/Results.vue'



export default {
  name: 'App',
  components: { 
    block,results
  },
  data(){
    return {
    isPlaying: false,
    delay:null,
    score:0,
    showResult:false,
    audio2:null
    
    }
  },

  methods:{
    start(){
      this.delay=2000+Math.random()*5000
      this.isPlaying=true
      console.log(this.delay)
      this.showResult=false
      const audio= new Audio(require('@/assets/fadl.mp3'))
      audio.play()
       this.audio2= new Audio(require('@/assets/fadlSong.mp3'))
    },
    endGame(w){  //هي الباراميتر العبرناه من بلوك فيو عنطريق الايميت فانكشن قيمت الكاونت w
      this.showResult=true
      this.isPlaying=false
      this.score=w
    }
  }
}
</script>

<style>
*{   font-family: 'Lemonada', cursive;
 }
#app {


  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}

.play-btn{
  background-color: white;
  color: black;
  border-radius: 10em;
  font-size: 17px;
  font-weight: 600;
  padding: 1em 2em;
  cursor: pointer;
  transition: all 0.3s ease-in-out;
  border: 1px solid black;
  box-shadow: 0 0 0 0 black;
}

.play-btn:hover {
  transform: translateY(-4px) translateX(-2px);
  box-shadow: 2px 5px 0 0 black;
}

.play-btn:active {
  transform: translateY(2px) translateX(1px);
  box-shadow: 0 0 0 0 rgb(0, 0, 0);
}

.play-btn[disabled]{
  opacity:0.2;
  cursor: not-allowed;
}
</style>
