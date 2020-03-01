<template>
    <div :class="$style.wrapper">
        <div :class="$style.boll"></div>
    </div>
</template>

<script>
import anime from 'animejs'

export default {
    methods: {
        async close() {
            let self = this
            const size = Math.max(self.$el.clientWidth, self.$el.clientHeight)*3
            return anime({
                targets: self.$el.firstChild,
                width: `${size}px`,
                height: `${size}px`,
                easing: 'easeInOutQuad',
                duration: 5*1000,
            }).finished
        }
    }
}
</script>

<style lang="scss" module>
@import 'assets/scss/settings.scss';

.wrapper {
    position: absolute;
    width: 100%;
    height: 100%;
    overflow: hidden;
}
.boll {
    position: absolute;
    top: 0%;
    right: 0%;
    background: radial-gradient(#fff, #fff, rgba(#fff, 0));
    border-radius: 50%;
    width: 0px;
    height: 0px;
    transform: translateY(-50%) translateX(50%);
}
</style>