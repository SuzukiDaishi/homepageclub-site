<template>
    <header :class="$style.container">
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
                            duration: 500,
                        }"
                        to >
                        {{ section }}
                    </nuxt-link>
                </slide-effect>
            </div>
        </nav>
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
    }
}
</script>

<style lang="scss" module>
@import '~assets/scss/settings.scss';

header.container {
    width: 100%;
    height: 100px;
    padding-right: 100px;
    padding-top: 30px;
    position: fixed;
    top: 0;
    left: 0;
    z-index:100;
}
nav.endblock {
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
    padding: 0 20px;
    font-size: 1.5em;
    text-decoration: none;
    color: $text-color;
    font-weight: lighter;
}
</style>