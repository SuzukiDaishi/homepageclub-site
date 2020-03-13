<template>
<span :class="$style.wrapper">
    <span :class="$style.inner">
        <slot />
    </span>
</span>
</template>

<script>
export default {
    props: {
        color: {
            type: String,
            default: 'black'
        }
    },
    computed: {
        styles () {
            return {
                '--color': this.color,
            }
        }
    }
}
</script>

<style lang="scss" module>

.wrapper {
    width: 100%;
    height: 100%;
    &::before {
        --color: black;
        z-index: 30 ;
        position: absolute ;
        top: 0 ;
        left: 0 ;
        content: "" ;
        width: 0% ;
        height: 100% ;
        background: var(--color) ;
        animation: slideIn 1s ease-in-out .5s forwards;
        transform: skewX(15deg) ;
    }
}
.inner {
    opacity: 0;
    animation: feedIn 1s ease-in-out .5s forwards;
}
@keyframes slideIn {
    0% {
        width: 0%;
    }
    50% {
        width: 100%;
        margin-left: 0%;
    }
    100% {
        margin-left: 100%;
        width: 0%;
    }
}
@keyframes feedIn {
    0% {
        opacity: 0;
    }
    50% {
        opacity: 0;
    }
    51% {
        opacity: 1;
    }
    100% {
        opacity: 1;
    }
}
</style>