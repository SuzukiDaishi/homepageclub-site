<template>
    <div :class="$style.wrapper">
        <fixed-header :sections="sections" :container="'slidebox'"/>
        <fixed-sidebar />
        <main id="slidebox" :class="$style.container">
            <section :class="[$style.area, $style.area_top]">
                    <h1 :class="$style.title">
                        <slide-effect> {{top.hello}} </slide-effect>
                    </h1>
            </section>
            <hr :class="$style.line"/>
            <section :id="sections[0]" :class="[$style.area]">
                <fade-effect tag="div" :scrollY="scrollY" :class="$style.mission_block">
                    <span > 
                        {{ mission.section }}
                    </span>
                    <h2>{{ mission.title }}</h2>
                    <article>{{ mission.content }}</article>
                </fade-effect>
            </section>
            <hr :class="$style.line"/>
            <section :id="sections[1]" :class="$style.area">
                <div>
                    aaaa
                </div>
            </section>
            <hr :class="$style.line"/>
            <section :id="sections[2]" :class="$style.area">
                <div>
                    bbb
                </div>
            </section>
            <hr :class="$style.line"/>
            <section :id="sections[3]" :class="$style.area">
                <div>
                    ccc
                </div>
            </section>
            <hr :class="$style.line"/>
            <section :id="sections[4]" :class="$style.area">
                <div>
                    dddd
                </div>
            </section>
        </main>
    </div>
</template>

<script>
import FixedHeader from '~/components/molecules/FixedHeader.vue'
import FixedSidebar from '~/components/molecules/FixedSidebar.vue'
import SlideEffect from '~/components/atomis/SlideEffect.vue'
import FadeEffect from '~/components/atomis/FadeEffect.vue'
import texts from '~/assets/configs/toppageTexts.json'

export default {
    components: {
        FixedHeader,
        FixedSidebar,
        FadeEffect,
        SlideEffect,
    },
    data() {
        return {
            sections: [
                texts['HEADER_MISSION'],
                texts['HEADER_SERVICE'],
                texts['HEADER_WORKS'],
                texts['HEADER_MEMBERS'],
                texts['HEADER_CONTACT'],
            ],
            top: {
                hello: texts['MISSION_TOP_HELLO']
            },
            mission: {
                section: texts['MISSION_SECTION'],
                title: texts['MISSION_TITLE'],
                content: texts['MISSION_CONTENT']
            },
            scrollY: 0,
        }
    },
    mounted() {
        let self = this
        this.$el.querySelector('#slidebox').onscroll = function() {
            self.handleScroll(this);
        }
    },
    methods: {
        handleScroll(event) {
            this.scrollY = event.scrollTop
        }
    }
}
</script>

<style lang="scss" module>
@import '~assets/scss/settings.scss';

.wrapper {
    width:100%;
    overflow: hidden;
    background: $bg-color;
}
.container {
    overflow: auto;
    scroll-snap-type: y mandatory;
    height: 100vh;
}
.area {
    scroll-snap-align: start;
    height: 100vh;
    width:100%;
    &_top {
        position:relative;
        width: 100%;
        height: 100%;
        & h1 {
            position:absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
        }
    }
}
.mission_block {
    &>article {
        white-space:pre-wrap;
        word-wrap:break-word;
    }
}
hr.line {
    width: 90%;
    height: 1px;
    background: $line-color;
    border: none;
}
h1.title {
    font-size: 2.5em;
    font-weight: 50;
}
</style>