<template>
  <div class="container flex-auto relative bg-black">
    <div class='absolute image top-0 bottom-0 right-0 left-0 z-1'></div>
    <div class='flex flex-column z-2'>
      <div class='white-card relative bg-white o-80 mt5 ml5'>
        <div class=' z-4 pa3 gray-1'>
          <div class='f2 b fw6'>I <br> BUILT <br>{<span class='special-text'>{{specialText[step]}}</span>} <br>USER INTERFACE</div> 
          <div class='fw3 f5 i'>a.k.a Front-End Developer</div>
        </div>
        
      </div>  
    </div>
      
  </div>
</template>

<script>
import { setInterval } from 'timers';


export default {
  data: function(){
    return {
      specialText: ["functional","clean","simple","intutive"],
      step: 0,
    }
  },
  mounted(){
    setInterval(()=>{
      if((this.specialText.length - 2) < this.step){
        this.step = 0;
      }else{
        this.step++;
      }
    },4000)
  }
}
</script>

<style>
.container {
  /* margin: 0 auto; */
  min-height: 100vh;
  display: flex;
  /* justify-content: center;
  align-items: center; */
  text-align: center;

}
.image{
  background-image: url('https://picsum.photos/id/1074/1400/700');
  background-size: cover;
  opacity: 0.80;
}

.white-card{
  width: 330px; /* 330 */
  /* height: 180px; */
  border: 1px solid transparent;
  border-radius: 5px;
  text-align: left;
}
.special-text{
  font-family: 'Courier New', Courier, monospace;
  font-weight: 300;
}
</style>
