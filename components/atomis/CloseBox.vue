<template>
    <div :class="$style.wrapper">
        <div :class="$style.animebox1"></div>
        <div :class="$style.animebox2"></div>
        <div :class="$style.animebox3"></div>
    </div>
</template>

<script>
import anime from 'animejs'

export default {
    methods: {
        async close() {
            let self = this
            anime({
                targets: self.$el.children[0],
                width: '125%',
                easing: 'easeInOutExpo',
                duration: 1500,
            })
            await this.sleep(100)
            anime({
                targets: self.$el.children[1],
                width: '125%',
                easing: 'easeInOutExpo',
                duration: 1500,
            })
            await this.sleep(100)
            return anime({
                targets: self.$el.children[2],
                width: '125%',
                easing: 'easeInOutExpo',
                duration: 1500,
            })
            .finished
        },
        async sleep(waitSeconds, someFunction=()=>{}) {
        return new Promise(resolve => {
          setTimeout(() => {
            resolve(someFunction())
          }, waitSeconds)
        })
      } 
    }
}
</script>

<style lang="scss" module>
@import '~assets/scss/settings.scss';

@mixin animebox($bgcolor: $bg-color) {
    position: absolute;
    top: 0%;
    right: 0%;
    background: $bgcolor;
    width: 0%;
    height: 100%;
    @include sp {
        transform: skewX(-10deg);
    }
    @include tab {
        transform: skewX(-10deg);
    }
    @include pc {
        transform: skewX(-20deg);
    }
    transform-origin: bottom left;
}

.wrapper {
    position: absolute;
    width: 100%;
    height: 100%;
    overflow: hidden;
}
.animebox1 {
    @include animebox($loader-effect-color1) ;
}
.animebox2 {
    @include animebox($loader-effect-color2) ;
}
.animebox3 {
    @include animebox() ;
}
</style>