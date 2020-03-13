<template>
    <component :is="tag" :class=" isRangeIn ? [$style.effect, $style.active] : $style.effect">
        <slot />
    </component>
</template>

<script>
export default {
    props: ['tag', 'scrollY'],
    data() {
        return {
            elementY: 0,
            range: 0,
        }
    },
    mounted() {
        if(this.scrollY === undefined) {
            this.$el.classList.add(this.$style.active)
        }
        this.handleResize()
        addEventListener('resize', this.handleResize)
    },
    computed: {
        isRangeIn() {
            return ( this.elementY - this.range < this.scrollY )
        }
    },
    methods: {
        handleResize() {
            this.elementY = this.$el.getBoundingClientRect().y
            this.range = innerHeight
        }
    }
}
</script>

<style lang="scss" module>
@import '~assets/scss/settings.scss';

.effect {
    opacity: 0;
}  
@keyframes fadeIn {
    from {
        opacity: 0;
        transform: translateY(20px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

.active {
    animation-name: fadeIn;
    animation-duration: 1s;
    animation-timing-function: linear;
    opacity: 1;
}
</style>