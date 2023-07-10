<template>
  
    <img class="shadow__btn" :src="require('@/assets/fadl.jpg')" @click="stopTimer" alt="fadl photo" v-if="showBlock">
  

</template>

<script>
export default {
 props:['delay','photo'],
 data(){
  return {
   showBlock: false,
   count: 0,
   timer:null,
  }
 },
 mounted(){

  setTimeout(()=>{
    this.showBlock = true
    this.stratTimer()
  },this.delay)
 },
 methods:{
  stratTimer(){

    this.timer= setInterval(()=> {
     this.count= this.count + 0.01
    }, 10) // Executes the callback function every 1000 milliseconds (1 second)

  },
 stopTimer(){
  clearInterval(this.timer)
  this.count=this.count.toFixed(2)
  console.log(this.count)
  this.showBlock=false
  this.$emit("end",this.count)
 }

 }

 

}

</script>

<style scoped>

*{font-family: 'Bungee Inline', cursive;}

 .shadow__btn {

  width: 400px;
  border: none;
  border-radius: 7px;
  transition-property: box-shadow;
  margin: 40px auto;
}

.shadow__btn {
  box-shadow: 0 0 25px rgb(0,140,255);
}

.shadow__btn:hover {
  box-shadow: 0 0 5px rgb(0,140,255),
              0 0 25px rgb(0,140,255),
              0 0 50px rgb(0,140,255),
              0 0 100px rgb(0,140,255);
}

</style>