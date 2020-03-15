<template>
    <header :class="$style.header_default">
        <div :class="$style.container" v-if="$device.isDesktopOrTablet">
            <nav :class="$style.endblock">
                <div :class="$style.endblock_inline">
                    <slide-effect>
                        <nuxt-link
                            v-for="(section, i) in sections"
                            :key="i" 
                            :class="$style.nav_item"
                            v-scroll-to="{
                                el: `#${section}`,
                                container: `#${container}`,
                                duration: 0,
                            }"
                            to >
                            {{ section }}
                        </nuxt-link>
                    </slide-effect>
                </div>
            </nav>
        </div>
        <div v-else :class="$style.sp_header">
                <div :class="$style.menu_trigger" @click="modalActive">
                    <slide-effect>
                        <div>
                            <span :class="$style.lines"></span>
                            <span :class="$style.lines"></span>
                            <span :class="$style.lines"></span>
                        </div>
                    </slide-effect>
                </div>
            <div :class="$style.sp_modal" v-if="isModal">
                <div :class="$style.x_trigger" @click="modalDeactive">
                    <span :class="$style.x_lines"></span>
                    <span :class="$style.x_lines"></span>
                </div>
            </div>
        </div>
    </header>
</template>

<script>
import FadeEffect from '~/components/atomis/FadeEffect.vue'
import SlideEffect from '~/components/atomis/SlideEffect.vue'

export default {
    props: ['sections', 'container'],
    components: {
        FadeEffect,
        SlideEffect,
    },
    data() {
        return {
            isModal: false
        }
    },
    methods: {
        modalActive() {
            this.isModal = true
        },
        modalDeactive() {
            this.isModal = false
        }
    }
}
</script>

<style lang="scss" module>
@import '~assets/scss/settings.scss';

.header_default {
    background: none;
}

.container {
    width: 100%;
    height: 100px;

    padding-right: 100px;
    @include tab {
        padding-right: 20px;
    }
    @include pc {
        padding-right: 100px;
    }
    padding-top: 30px;
    position: fixed;
    top: 0;
    left: 0;
    z-index:100;
}
.endblock {
    display: flex;
    justify-content: flex-end;
    align-items: center;
    list-style: none;
}
.endblock_inline {
    position: relative;
    height: 40px;
}
.nav_item {
    @include tab {
        padding: 0 15px;
    }
    @include pc {
        padding: 0 20px;
    }
    font-size: 1.5em;
    text-decoration: none;
    color: $text-color;
    font-weight: lighter;
}

.sp_header {
}

.menu_trigger {
    z-index: 100;
    display: inline-block;
    box-sizing: border-box;
    position: fixed;
    top: 0;
    left: 0;
    width: 80px;
    height: 80px;
}

.lines {
    position: absolute;
    background: black;  
    left: 10px; 
    height: 1px;
    &:nth-child(1) {
        top: 20px;
        width: 60px;
    }
    &:nth-child(2) {
        top: 40px;
        width: 50px;
    }
    &:nth-child(3) {
        top: 60px;
        width: 40px;
    }
    opacity: 0;
    animation: feedIn 1s ease-in-out .5s forwards;
}

.x_trigger {
    z-index: 300;
    display: inline-block;
    box-sizing: border-box;
    position: fixed;
    top: 0;
    left: 0;
    width: 80px;
    height: 80px;
}

.x_lines {
    position: absolute;
    background: black;  
    left: 10px; 
    height: 1px;
    &:nth-child(1) {
        transform: rotate(315deg);
        top: 40px;
        width: 50px;
        transform: rotate(315deg);
    }
    &:nth-child(2) {
        top: 40px;
        width: 50px;
        transform: rotate(-315deg);
    }
}

.sp_modal {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    background: rgb(245, 255, 224);
    z-index: 200;
}

@keyframes feedIn {
    0% { opacity: 0; }
    50% { opacity: 0; }
    51% { opacity: 1; }
    100% { opacity: 1; }
}
</style>