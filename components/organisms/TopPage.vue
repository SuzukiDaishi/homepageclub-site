<template>
    <div :class="$style.wrapper">
        <fixed-header :sections="sections" :container="'slidebox'" />
        <fixed-sidebar />
        <main id="slidebox" :class="$style.container">
            <section id="top" :class="[$style.area, $style.area_top]">
                <h1>こんにちわ、ホームページ倶楽部です。</h1>
            </section>
            <section :id="sections[0]" :class="$style.area" style="background:blue;"></section>
            <section :id="sections[1]" :class="$style.area" style="background:green;"></section>
            <section :id="sections[2]" :class="$style.area" style="background:red;"></section>
            <section :id="sections[3]" :class="$style.area" style="background:blue;"></section>
            <section :id="sections[4]" :class="$style.area" style="background:green;"></section>
        </main>
    </div>
</template>

<script>
import FixedHeader from '~/components/molecules/FixedHeader.vue'
import FixedSidebar from '~/components/molecules/FixedSidebar.vue'
import texts from '~/assets/configs/toppageTexts.json'

export default {
    components: {
        FixedHeader,
        FixedSidebar,
    },
    data() {
        return {
            sections: [
                texts['HEADER_MISSION'],
                texts['HEADER_SERVICE'],
                texts['HEADER_WORKS'],
                texts['HEADER_MEMBERS'],
                texts['HEADER_CONTACT'],
            ]
        }
    }
}
</script>

<style lang="scss" module>
@import '~assets/scss/settings.scss';

.wrapper {
    width:100%;
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
        &>h1 {
            position:absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
        }
    }
}

</style>