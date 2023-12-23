<template>
    <div class="block" v-if="showBlock" @click="endTimer">
        click me
    </div>
</template>

<script>
//lifecycle of components and hooks
export default {
    props:['delay'],
    data(){
        return {
            showBlock:false,
            timer:null,
            reactionTime:0
        }

    },
    mounted() {
        console.log('component mounted');
        this.startTimer();
        setTimeout(() => this.showBlock = true, this.delay);
    },
    methods:{
        startTimer()
        {
            this.timer = setInterval(()=>{
                this.reactionTime += 10;
            }, 10)

        },
        endTimer()
        {
            clearInterval(this.timer)
            this.$emit('end',this.reactionTime);
            // console.log(this.reactionTime)
        }
    }
    // updated() {

    //     console.log('updated block');


    // },
    // unmounted(){
    //     console.log("Component has been removed from DOM");
    // }
 
}
</script>
<style>
.block {
    width: 400px;
    border-radius: 20px;
    background: #48bcc7;
    color: white;
    text-align: center;
    padding:100px 0;
    margin: 40px auto;

}
</style>
