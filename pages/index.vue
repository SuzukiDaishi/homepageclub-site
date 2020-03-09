<template>
    <div class="container">
        <loader-full-screen />
    </div>
</template>

<script>
import LoaderFullScreen from '~/components/organisms/LoaderFullScreen.vue'

export default {
    components: {
        LoaderFullScreen,
    }
}
</script>

<style lang="scss">
@import '~assets/scss/settings.scss';

.container {
    width: 100vw;
    height: 100vh;
    background: $loader-bg-color;
}
</style>
