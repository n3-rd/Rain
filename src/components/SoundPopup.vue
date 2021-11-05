<template>
    <div class="full-height full-weight app-bg-brand">

<div class="absolute-center full-width">
<div class="text-center text-weight-bold text-white q-my-lg playing-sound-name">{{soundName}}</div>
<q-icon name="stop_circle" animation='pulse' class="text-white text-center cursor-pointer stop-icon" @click="stopMusic" />
</div>

    </div>
</template>

<script>
export default {
    props:{
        soundName: String
    },
        methods:{
stopMusic: function(){
    Howler.stop()
    // this.$parent.this.isMusicPlaying()
    this.$.parent.parent.parent.parent.parent.data.soundDialog = false
    // this.$.parent.parent.parent.parent.parent.data.soundPlaying = false
    // this.$.parent.parent.parent.parent.parent.ctx.isMusicPlaying()

}
        },
        created(){
            // console.log(this.$.parent.parent.parent.parent.parent.ctx.isMusicPlaying)
            
        }
}
</script>
<style lang="scss">
.playing-sound-name{
    font-size: 3.4rem;
    display: block;
    opacity: 0.7;
}
.stop-icon{
    margin: 0 auto;
display: block;
font-size: 7.1rem;
opacity: 0.9;
}
</style>