<script>
export default {
  data() {
    return {
      isDay: true
    };
  },
  methods:{
    onDayChange(){
      this.isDay = !this.isDay
    }
  }
};
</script>

<template>
  <h1>HelloWorld</h1>
  <h2 v-if="isDay">It's sunny outside!</h2>
  <h2 v-else> It's dadrk
    outside!</h2>

    <template v-if="isDay">
  <h1>
  Welcome to My Awesome Page
  </h1>
  <p>
  Hello there! This is a cool Vue.js
  example.
  </p>
  <p>
  Let's explore some awesome features
  together!
  </p>
  </template>
  <p v-else>
Click the button above to reveal the
exciting content!
</p>

    <button @click="onDayChange">
      Togle time
    </button>
<h2 v-show="isDay">
  THIS SHOULD BE HIDDEN WHEN IS DAY
</h2>

</template>


