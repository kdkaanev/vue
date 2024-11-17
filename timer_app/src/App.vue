<script>
const parseTimerInput = (text)=>{
  const [h, m, s] = text.split(':').map(num => Number(num ));
  return s + 60 * m + 3600 * h;
}
export default {
  data() {
    return {
      userInput: '',
      timerSeconds: 0,
      referenceSeconds: 0,
      showWarning: false,
    };

  },
  watch: {
    timerSeconds(newValue) {
      if (this.showWarning)
        return;

      if (newValue < (this.referenceSeconds * 0.2)){
        this.showWarning = true;
      }
    }

  },


  methods:{
    onInput(event){
      this.userInput = event.target.value;
    },
    onStart(){

      this.timerSeconds = parseTimerInput(this.userInput);
      this.referenceSeconds = parseTimerInput(this.userInput);
      this.handlerTimer()

    },
    handlerTimer(){
       const interval = setInterval(()=>{
        if(this.timerSeconds > 0){
          this.timerSeconds -= 1;
        }
        else {
          clearInterval(interval);
          this.onReset()
        }
      }, 1000)
    },
    onPause(){
    },
    onReset(){
      this.timerSeconds = 0;
      this.referenceSeconds = 0;
      this.userInput = ''
      this.showWarning = false;
    },

  },
}
</script>

<template>
  <h1>My Timer</h1>
  <input type="text" @input="onInput">
  <button type="button" @click="onStart">Start</button>
  <button type="button" @click="onPause">Pause</button>
  <button type="button" @click="onReset">Reset</button>

  <p> Remaining Time {{ timerSeconds }}</p>
  <p v-if="showWarning">
    Les than 20% remaining!
  </p>
</template>