<template>
  <div class="container flex-auto relative bg-black">
    <div class='absolute image top-0 bottom-0 right-0 left-0 z-1'></div>
    <div class='flex flex-column z-2 relative pa3 flex-auto'>
      <div 
          class='white-card absolute bg-white o-80 mt5 ml5'
          :style='{top:cardPostion.top, left:cardPostion.left}'>
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
      specialText: ["functional","clean","simple","intuitive"],
      step: 0,
      cardPostion: {
        top:'5%',
        left: '12%',
      },
      progressionValue: [0.010,0.017,0.029,0.014,0.023,0.025,0.027],
      progressionValue2: [0.014,0.010,0.020,0.0250,0.026,0.022,0.029],
      progressionValueSeconds:[1,2,3,4,5,6,7],
      randomNumber: [0,1,2],
      showEffect: true
    }
  },
  methods: {
    getRandomInt: function(min, max) {
      min = Math.ceil(min);
      max = Math.floor(max);
      return Math.floor(Math.random() * (max - min)) + min; 
    }
  },
  mounted(){
    
    let mode = true;
    setInterval(()=>{
      let val = Number(this.cardPostion.top.split('%')[0]);//0.025
      if(mode){
        val = val + this.progressionValue[this.randomNumber[0]];
      }else{
        val = val - this.progressionValue2[this.randomNumber[1]];
      }
       this.cardPostion.top = val + '%';
      
       if(val > 60){
         mode = false;
         this.randomNumber = [this.getRandomInt(0,7),this.getRandomInt(0,7),this.getRandomInt(0,7)];
         this.step = this.getRandomInt(0,this.specialText.length);
       }
       if(val < 0){
         mode = true;
         this.randomNumber = [this.getRandomInt(0,7),this.getRandomInt(0,7),this.getRandomInt(0,7)];
        this.step = this.getRandomInt(0,this.specialText.length);
       }
      //  val < 0 && (mode = true);
    },this.progressionValueSeconds[this.randomNumber[2]]);

    //
    let mode2 = true;
    setInterval(()=>{
      let val = Number(this.cardPostion.left.split('%')[0]);//0.025
      if(mode2){
        val = val + this.progressionValue2[this.randomNumber[0]];
      }else{
        val = val - this.progressionValue[this.randomNumber[1]];
      }
       this.cardPostion.left = val + '%';
      
       if(val > 60){
         mode2 = false;
         this.randomNumber = [this.getRandomInt(0,7),this.getRandomInt(0,7),this.getRandomInt(0,7)];
        this.step = this.getRandomInt(0,this.specialText.length);
       }
       if(val < 0){
         mode2 = true;
         this.randomNumber = [this.getRandomInt(0,7),this.getRandomInt(0,7),this.getRandomInt(0,7)];
         this.step = this.getRandomInt(0,this.specialText.length);
       }
      //  val < 0 && (mode = true);
    },this.progressionValueSeconds[this.randomNumber[2]]);
  },
  async created(){
    if(this.showEffect){
      const { data } = await this.$axios.get('https://api.datamuse.com/words?ml=functional');
      let filtered = data.filter(x => x.tags.includes("adj") && x.score > 70000).map(x => x.word);
      this.specialText = [...this.specialText,...filtered];
    }
    
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
  width: 350px; /* 330 */
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
