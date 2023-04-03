<template>
  <div class="block" v-if="showBlock" @click="stopTimer" :style="{ width: size + 'px', height: size + 'px', borderRadius: '50%', position: 'absolute', top: topPos + 'px', left: leftPos + 'px' }"></div>
</template>

<script>
export default {
  props: ['delay'],
  data(){
    return {
      showBlock:false,
      timer: null,
      reactionTime: null,
      size:0,
      topPos:0,
      leftPos:0
    }
  },
  mounted() {
          // Generate random values for topPos and leftPos
    this.size = Math.floor(Math.random() * 100) + 200; // generate a random size between 50 and 150
    this.size = Math.round(this.size / 2) * 2;
    console.log(this.size)

     // get the width and height of the parent element
    const parentWidth = this.$el.parentElement.offsetWidth;
    const parentHeight = this.$el.parentElement.offsetHeight;

    // generate random positions for top and left properties
    this.topPos = Math.floor(Math.random() * (parentHeight - this.size));
    this.leftPos = Math.floor(Math.random() * (parentWidth - this.size));

    setTimeout(()=> {
      this.showBlock = true
      this.startTimer()
      console.log(this.delay)
    }, this.delay)
  },

  methods: {
    startTimer () {
      this.timer = setInterval(()=>{
        this.reactionTime+=10
      },10)
    },
    stopTimer(){
      clearInterval(this.timer)
      console.log(this.reactionTime)
      this.$emit('end', this.reactionTime)
    }
  }
}
</script>

<style>
  .block {
    /* width: 400px;
    height: 300px; */
    /* border-radius: 20px; */
    background: #0faf87;
    color: white;
    text-align: center;
    /* padding: 100px 0; */
    margin: 40px auto;
  }
</style>