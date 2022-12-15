<template>
    <div class="newyear">
        <div class="modal-wrapper" :class="{ 'vis': isOpen }"></div>
        <ModalPresent class="modal-pos" :class="{ 'toLeft': curdata.left }" v-show="isOpen" :data="curdata"
            @close="close" />
        <h3 class="newyear-title">Новогодний подарок ждёт тебя под ёлкой</h3>
        <div v-for="i in boxList" :key="i.num" class="boxWrapper"
            :class="[i.class, i.num == curdata.num ? 'chosenBox' : '']" @click="actived(i)">
            <BoxPresent :num="i.num" :close-box="closeBox" />
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
                    mail: '*Твой Тайный Санта оформит тебе подписку в течение 2-х рабочих дней.',
                    left: true
                }, {
                    class: 'second',
                    num: 2,
                    title: 'VPN SurfShark',
                    subtitle: 'Подключение ко всем расширенным функциям VPN на полгода',
                    mail: '*Cсылка для скачивания и активации придёт тебе на почту в течение 2-х рабочих дней.', left: false
                }, {
                    class: 'third',
                    num: 3,
                    title: 'ЛитРес',
                    subtitle: 'Электронный подарочный сертификат на лучшие книги',
                    mail: '*Сертификат придёт тебе на почту в течение 2-х рабочих дней.', left: true
                }, {
                    class: 'forth',
                    num: 4,
                    title: 'Ляг.Спиной',
                    subtitle: 'Сертификат на 1 сеанс массажа классика/спорт/релакс/лицо',
                    mail: '*Сертификат придёт тебе на почту в течение 2-х рабочих дней. Сертификат действует 2 месяца.', left: true
                }, {
                    class: 'fifth',
                    num: 5,
                    title: 'Менталитет',
                    subtitle: 'Электронный сертификат на 5000₽ в ресторан Менталитет',
                    mail: '*Для бронирования столика позвоните по номеру +7 903 017-73-88. При посещении предъявите сертификат.', left: false
                }, {
                    class: 'sixth',
                    num: 6,
                    title: 'Amediateka',
                    subtitle: 'Индивидуальная подписка на 6 месяцев',
                    mail: '*Cсылка для активации подписки придёт тебе на почту в течение 2-х рабочих дней.', left: false
                },
            ],
            curdata: {
                class: 'first',
                num: 1,
                title: 'Telegram Premium',
                subtitle: 'Подписка на 12 месяцев',
                left: true
            },
            isOpen: false,
            closeBox: false
        }
    },
    methods: {
        actived(data) {
            this.isOpen = true
            this.curdata = data
            this.closeBox = false
        },
        close() {
            this.isOpen = false
            this.closeBox = true
        }
    },
}
</script>

<style lang="scss">
.modal-wrapper {
    background-color: rgba(0, 0, 0, 0.3);
    visibility: hidden;
    position: fixed;
    z-index: 90;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    overflow: auto;

    &.vis {
        visibility: visible;
    }
}

.modal-pos {
    position: fixed;
    right: 5%;
    top: 50%;
    z-index: 110;
    transform: translateY(-50%);

    &.toLeft {
        right: auto;
        left: 5%;

        @media screen and (max-width:725px) {
            left: 5%;
            right: auto;
            transform: translateY(-50%);
        }
    }

    @media screen and (max-width:725px) {
        left: 5%;
        right: auto;
        transform: translateY(-50%);
    }
}

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

    @media screen and (max-width:680px) {
        min-height: 633px;
        margin-top: 20px;
        max-width: 90%;
    }

    @media screen and (max-width:550px) {
        margin-top: 85px;
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
            right: 40px;
        }

        @media screen and (max-width:680px) {
            max-width: 100px;
            right: 30px;
        }

        @media screen and (max-width:450px) {
            max-width: 85px;
            right: 10px;
        }
    }

    .second {
        max-width: 240px;
        left: 250px;
        bottom: 20px;
        z-index: 10;

        @media screen and (max-width:1325px) {
            max-width: 140px;
            left: 236px;
            bottom: 15px;
        }

        @media screen and (max-width:680px) {
            max-width: 131px;
            left: 160px;
            bottom: 15px;
        }

        @media screen and (max-width:450px) {
            max-width: 114px;
            left: 61px;
        }
    }

    .third {
        max-width: 315px;
        right: 30px;
        bottom: 9px;
        z-index: 9;

        @media screen and (max-width:1325px) {
            max-width: 215px;
            right: 80px;
        }

        @media screen and (max-width:680px) {
            max-width: 167px;
            right: 70px;
        }

        @media screen and (max-width:450px) {
            max-width: 145px;
            left: 186px;
        }
    }

    .forth {
        max-width: 215px;
        right: 260px;
        z-index: 10;

        @media screen and (max-width:1325px) {
            max-width: 115px;
            right: 240px;
        }

        @media screen and (max-width:680px) {
            max-width: 94px;
            right: 190px;
        }

        @media screen and (max-width:450px) {
            max-width: 74px;
            left: 145px;
        }
    }

    .fifth {
        max-width: 195px;
        left: 140px;
        bottom: 30px;
        z-index: 8;

        @media screen and (max-width:1325px) {
            max-width: 100px;
            left: 170px;
        }

        @media screen and (max-width:680px) {
            max-width: 89px;
            left: 115px;
        }

        @media screen and (max-width:450px) {
            max-width: 80px;
            left: 35px;
        }
    }

    .sixth {
        max-width: 218px;
        left: 25px;
        bottom: 15px;
        z-index: 8;

        @media screen and (max-width:1325px) {
            max-width: 115px;
            left: 105px;
        }

        @media screen and (max-width:680px) {
            max-width: 106px;
            left: 55px;
        }

        @media screen and (max-width:450px) {
            max-width: 90px;
            left: 0px;
        }
    }

    .chosenBox {
        z-index: 103;
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

    @media screen and (max-width:550px) {
        font-size: 20px;
        line-height: 24px;
    }
}
</style>