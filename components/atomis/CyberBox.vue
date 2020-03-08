<template>
<div :class="$style.cyber_bg">
    <slot />
</div>
</template>

<script>
export default {

}
</script>

<style lang="scss" module>
@import '~assets/scss/settings.scss';

.cyber_bg {
    width: 100%;
    height: 100%;
    overflow: hidden;
    background-image: url('~assets/images/cyberLine.svg');
    background-size: cover;
    color: $bg-color;
}
</style>
