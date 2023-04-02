<template>
  <h3>Your result time: {{ score }} ms</h3>
  <h4>Your rank: {{ rank }}</h4>

</template>

<script>
export default {
  props:['score'],
  data(){
    return{
      rank:null
    }
  },
  mounted(){
    if (this.score < 250){
      this.rank = 'Too fast!'
    } else if (this.score < 400) {
      this.rank = "Almost fast!"
    } else {
      this.rank = "Hmmm...not that fast :("
    }
  }
}
</script>

<style>

</style>