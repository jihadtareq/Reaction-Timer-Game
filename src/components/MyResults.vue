<template>
  <div>
    <h4>Your Score</h4>
    <p>{{ score }} ms</p>

    <h2 class="rank">{{ rank }}</h2>
    
  </div>

</template>
<script>

export default {
    props:['score'],
    data() {
      return {
        rank:null,
      }
    },
    mounted() {
      if(this.score < 3000) {
        this.rank = 'Danger Zone';
      } else if(this.score < 4500) {
        this.rank = "You're Doing Alright";
      }else{
        this.rank = 'Snail pace..!';
      }
    }
}
</script>
<style>
.rank {
  color: rgb(87, 200, 163);
}

</style>
