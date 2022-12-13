<template>
    <div class="adslides ticker-wrapper">
        <div class="ticker-wrapper__first-half">
            <p>Меньше задач, больше доходов</p>
            <p class="slash">/</p>
            <p>Низкого CPI</p>
            <p class="slash">/</p>
            <p>Низкого ДРР</p>
            <p class="slash">/</p>
            <p>Высокого LTV</p>
            <p class="slash">/</p>
            <p>Высокого ROI</p>
            <p class="slash">/</p>
            <p>Работающих гипотез</p>
            <p class="slash">/</p>
            <p>Успешных кампаний</p>
            <p class="slash">/</p>
            <p>Эффективных стратегий</p>
            <p class="slash">/</p>
            <p>Меньше скучных звонков</p>
            <p class="slash">/</p>
            <p>Больше продаж</p>
            <p class="slash">/</p>
            <p>Меньше правок</p>
            <p class="slash">/</p>
            <p>Больше кликов</p>
            <p class="slash">/</p>
            <p>Успешных тестов</p>
            <p class="slash">/</p>
            <p>Хороших коллег</p>
            <p class="slash">/</p>
        </div>
        <!-- <div class="ticker-wrapper__second-half">
            <p class="slash">/</p>
            <p>Эффективных стратегий</p>
            <p class="slash">/</p>
            <p>Меньше скучных звонков</p>
            <p class="slash">/</p>
            <p>Больше продаж</p>
            <p class="slash">/</p>
            <p>Меньше правок</p>
            <p class="slash">/</p>
            <p>Больше кликов</p>
            <p class="slash">/</p>
            <p>Успешных тестов</p>
            <p class="slash">/</p>
            <p>Хороших коллег</p>
            <p class="slash">/</p>
        </div> -->

    </div>
</template>
<style lang="scss">
.slash{
    margin: 0 10px;
}
.adslides {
    background: #FF7323;
    overflow: hidden;
    height: 47px;
    position: relative;
    text-align: center;
    font-size: 18px;
    line-height: 20px;
    font-weight: 300;
    .ticker-wrapper__first-half p:nth-child(odd){
            min-width: 200px;
        }
        .ticker-wrapper__second-half p:nth-child(even){
            min-width: 200px;
        }
    @media screen and (max-width:1325px) {
        font-size: 13px;
        line-height: 17px;
        
    }
    div {
        display: flex;
        flex-direction: row;
        justify-content: space-around;
        align-items: center;
        // overflow: hidden;
        width: 100%;
        height: 47px;
        transform: translate(100%, 0);


    }

    $duration: 20s;

    .ticker-wrapper__first-half,
    .ticker-wrapper__second-half {
        display: flex;
        flex-direction: row;
        justify-content: space-around;
        align-items: center;
        position: absolute;
        top: 0;
        right: 0;
        animation: ticker $duration*2 infinite linear forwards;
    }

    .ticker-wrapper__second-half {
        animation: $duration/2 ticker $duration infinite linear forwards;
    }
}

@keyframes ticker {
    0% {
        transform: translate(100%, 0);
    }

    50% {
        transform: translate(0, 0);
    }

    100% {
        transform: translate(-100%, 0);
    }
}
</style>