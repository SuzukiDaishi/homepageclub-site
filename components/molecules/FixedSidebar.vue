<template>
    <aside :class="$style.container">
        <span :class="$style.copy_text">{{ designedBy }}</span>
    </aside>
</template>

<script>
import texts from '~/assets/configs/toppageTexts.json'

export default {
    data() {
        return {
            designedBy: texts['DESIGNED_BY']
        }
    }
}
</script>

<style lang="scss" module>
.container {
    position: fixed;
    top: 0;
    right: 0;
    transform: rotate(0.25turn) translate(350px, -240px);
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
        background: #444;
        display: block;
        margin-left: 20px;
    }
}
</style>