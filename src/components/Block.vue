<template>
 <div class="block" v-if="showBlock" @click="clearTimer">
      <h4>Click Me</h4>
      {{delay}}
</div> 
</template>

<script>
export default {
    name: 'Block',
    data() {
        return {
           showBlock:false,
           timer:null,
           reactionTime:0

        }
    },
    props:[ 'delay' ],
    mounted()
    {
        setTimeout(()=> {
            this.showBlock=true;
            this.startTimer();
        },this.delay);
    },
    methods:
    {
        startTimer()
        {
            this.timer=setInterval(()=> {
                this.reactionTime+=10;
            },10);
        },
        clearTimer()
        {
            clearInterval(this.timer);
            console.log(this.reactionTime);
            this.$emit('end',this.reactionTime);
        }
    }

}
</script>

<style scoped>
.block {
    background-color: aquamarine;
    color: blueviolet;
    margin:50px auto;
    text-align: center;
    width: 400px;
    height: 200px;
}

</style>