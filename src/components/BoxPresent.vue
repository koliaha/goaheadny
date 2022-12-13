<template>
    <div class="present-item" :class="{'isOpen':isOpen}" @click="(isOpen = !isOpen)">
        <img v-if="!isOpen" :src="require(`@/assets/img/presents/${num}.png`)" alt="">
        <img v-else  :src="require(`@/assets/img/presents/open${num}.png`)" alt="">
    </div>
</template>
<script>

export default {
    
    props:["num"],
    data() {
        return {
            isOpen: false
        }
    },
}
</script>
<style lang="scss">
.present-item {
    position: absolute;
    bottom: 0;
    cursor: pointer;
    filter: grayscale(100%);
    transition: 0.4s;
    user-select: none;
    &:hover {
        filter: none
    }
    img {
        width: 100%;
    }

    &.isOpen{
        filter: none;
        transform: scale(1.1);
        z-index: 15;
    }
}
</style>