<template>
    <div class="present-item" :class="{ 'isOpen': isOpen }" @click="(isOpen = !isOpen)">
        <div class="img-box" v-if="!isOpen">
            <img :src="require(`@/assets/img/presents/${num}.png`)" alt="">
        </div>
        <div class="img-box openedBox" v-else>
            <img class="openBoxBig" :src="require(`@/assets/img/presents/open${num}.png`)" alt="">
            <!-- <img v-if="isOpen" class="sunStar" :src="require(`@/assets/img/sun.png`)" alt=""> -->
        </div>

    </div>
</template>
<script>

export default {

    props: ["num", "closeBox"],
    data() {
        return {
            isOpen: false
        }
    },
    watch: {
        closeBox(val) {
            console.log('sadsadsa', val)
            if (val) this.isOpen = !val
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
    z-index: 110;

    &:hover {
        filter: none
    }

    .img-box {
        // position: absolute;
        width: 100%;
        height: 100%;
        left: 0;
        top: 0;
        z-index: 112;
    }

    img {
        width: 100%;
    }

    &.isOpen {
        filter: none;
        transform: scale(1.1);
        z-index: 1001;
    }

    // .openedBox {
    //     position: relative;
    //     width: 100%;
    //     height: 100%;
    // }

    // .openBoxBig {
    //     position: absolute;
    //     width: 200px;
    //     top: 0;
    //     left: 0;
    //     z-index: 120;
    // }

    .sunStar {
        position: absolute;
        left: 0;
        top: 0;
        z-index: 100;
    }
}
</style>