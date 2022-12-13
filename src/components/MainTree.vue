<template>
    <div class="newyear">
        <ModalPresent v-show="isOpen" :data="curdata" @close="close" />
        <h3 class="newyear-title">Новогодний подарок ждёт тебя под ёлкой</h3>
        <div v-for="i in boxList" :key="i.num" class="boxWrapper" :class="i.class" @click="actived(i)">
            <BoxPresent :num="i.num" />
        </div>
    </div>
</template>
<script>
import BoxPresent from './BoxPresent'
import ModalPresent from './ModalPresent.vue'
export default {
    components: {
        BoxPresent, ModalPresent
    },
    data() {
        return {
            boxList: [
                {
                    class: 'first',
                    num: 1,
                    title: 'Telegram Premium',
                    subtitle: 'Подписка на 12 месяцев',

                }, {
                    class: 'second',
                    num: 2,
                    title: 'VPN SurfShark',
                    subtitle: 'Подключение ко всем расширенным функциям VPN на полгода',
                }, {
                    class: 'third',
                    num: 3,
                    title: 'ЛитРес',
                    subtitle: 'Электронный подарочный сертификат на лучшие книги',
                }, {
                    class: 'forth',
                    num: 4,
                    title: 'Ляг.Спиной',
                    subtitle: 'Сертификат на 1 сеанс массажа классика/спорт/релакс/лицо',
                }, {
                    class: 'fifth',
                    num: 5,
                    title: 'Менталитет',
                    subtitle: 'Электронный сертификат на 5000₽ в ресторан Менталитет',
                }, {
                    class: 'sixth',
                    num: 6,
                    title: 'Amediateka',
                    subtitle: 'Индивидуальная подписка на 6 месяцев',
                },
            ],
            curdata: {
                class: 'first',
                num: 1,
                title: 'Telegram Premium',
                subtitle: 'Подписка на 12 месяцев',

            },
            isOpen: false
        }
    },
    methods: {
        actived(data) {
            this.isOpen = true
            this.curdata = data
        },
        close() {
            this.isOpen = false
        }
    },
}
</script>

<style lang="scss">
.newyear {
    min-height: 875px;
    position: relative;
    background: url('@/assets/img/elka.png');
    background-repeat: no-repeat;
    background-size: auto 100%;
    background-position: center;
    max-width: 900px;
    width: 100%;
    margin: 0 auto;
    margin-top: 95px;

    @media screen and (max-width:1325px) {
        min-height: 633px;
        margin-top: 40px;
        max-width: 700px;
    }

    .boxWrapper {
        position: absolute;
        width: 100%;
        bottom: 0;
    }

    .first {
        max-width: 148px;
        right: 0;
        z-index: 10;

        @media screen and (max-width:1325px) {
            max-width: 120px;
        }
    }

    .second {
        max-width: 240px;
        left: 250px;
        bottom: 20px;
        z-index: 10;
        @media screen and (max-width:1325px) {
            max-width: 140px;
        }
    }

    .third {
        max-width: 315px;
        right: 30px;
        bottom: 9px;
        z-index: 9;
        @media screen and (max-width:1325px) {
            max-width: 215px;
        }
    }

    .forth {
        max-width: 215px;
        right: 260px;
        z-index: 10;
        @media screen and (max-width:1325px) {
            max-width: 115px;
        }
    }

    .fifth {
        max-width: 195px;
        left: 140px;
        bottom: 30px;
        z-index: 8;
        @media screen and (max-width:1325px) {
            max-width: 100px;
        }
    }

    .sixth {
        max-width: 218px;
        left: 25px;
        bottom: 15px;
        z-index: 8;
        @media screen and (max-width:1325px) {
            max-width: 115px;
        }
    }

}

.newyear-title {
    max-width: 500px;
    width: 100%;
    font-weight: 500;
    font-size: 35px;
    line-height: 42px;
    text-align: center;
    position: absolute;
    left: 50%;
    top: 0;
    transform: translateX(-50%);
}
</style>