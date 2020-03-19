<template>
    <div>
        <div v-if="$device.isMobile && isSmart" style="height:50px"></div>
        <div v-else-if="$device.isMobile" style="height:70px"></div>
        <div v-else :class="$style.space"></div>
    </div>
</template>

<script>
export default {
    props: {
        isSmart: {
            type: Boolean,
            default: false
        }
    },
}
</script>

<style module>
.space {
    height: 100px;
}
</style>