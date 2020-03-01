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
.cyber_bg {
    width: 100%;
    height: 100%;
    background-image: url('~assets/images/cyberLine.svg');
    background-size: cover;
    color: white;
}
</style>
