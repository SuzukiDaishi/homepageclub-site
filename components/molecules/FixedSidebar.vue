<template>
    <aside :class="$style.container">
        <slide-effect :class="$style.copy_text">
            {{ designedBy }}
        </slide-effect>
    </aside>
</template>

<script>
import SlideEffect from '~/components/atomis/SlideEffect.vue'
import texts from '~/assets/configs/toppageTexts.json'

export default {
    data() {
        return {
            designedBy: texts['DESIGNED_BY']
        }
    },
    components: {
        SlideEffect,
    }
}
</script>

<style lang="scss" module>
@import '~assets/scss/settings.scss';

.container {
    position: fixed;
    top: 0;
    right: 0;
    transform: rotate(0.25turn) translate(300px, -280px);
    @include tab {
        transform: rotate(0.25turn) translate(400px, -240px);
    }
    @include pc {
        transform: rotate(0.25turn) translate(350px, -240px);
    }
}
.copy_text {
    display: flex;
    align-items: center;
    white-space: nowrap;
    &:after {
        content: "";
        flex-grow: 1;
        height: 1px;
        width: 300px;
        @include tab {
            width: 300px;
        }
        @include pc {
            width: 300px;
        }
        background: #444;
        display: block;
        margin-left: 20px;
        opacity: 0;
        animation: feedIn 1s ease-in-out .5s forwards;
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