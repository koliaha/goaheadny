<template>
    <div class="header">
        <div class="header-logo">
            <img src="@/assets/img/logo.svg" alt="">
        </div>
        <div class="header-title">
            <h1>Что объединяет <img src="@/assets/img/tree.svg" alt="" /> Новый год <br/> и <img src="@/assets/img/meta.svg"
                    alt="" /> Метавселенную? </h1>
        </div>
        <div class="header-subtitle">
            <p>
                Они - символ будущего, новых надежд и планов. Точно не знаешь,
                что принесет Новый год, и какие тайны хранит Метавселенная.
                Но чувствуешь, что мечты сбудутся, а в digital-реальности скучно
                определенно не будет. Желаем креативных идей, новых впечатлений
                и неиссякаемой энергии.
                <br />
                <br />
                С Новым годом!
            </p>
        </div>
    </div>
</template>
<style lang="scss">
.header {
    padding-top: 55px;
    text-align: center;
    display: flex;
    flex-direction: column;
    align-items: center;
    max-width: 1290px;
    justify-content: center;
    margin: 0 auto;
}

.header-logo {
    max-width: 150px;
    width: 100%;
    margin: 0 auto;
    margin-bottom: 45px;

    @media screen and (max-width:1325px) {
        margin-bottom: 0px;
    }

    @media screen and (max-width:650px) {
        max-width: 100px;
    }

    img {
        width: 100%;
    }
}

.header-title {
    font-weight: 300;
    font-size: 44px;
    line-height: 85px;
    margin-bottom: 41px;

    @media screen and (max-width:1325px) {
        font-size: 30px;
        line-height: 70px;
        margin-bottom: 20px;
    }

    @media screen and (max-width:1125px) {
        font-size: 23px;
        line-height: 50px;

        img {
            max-width: 70px;
        }
    }

    @media screen and (max-width:650px) {
        font-size: 17px;
        line-height: 40px;
        margin: 65px 0 32px;
        img {
            max-width: 40px;
        }
    }

    @media screen and (max-width:520px) {
        font-size: 12px;
        line-height: 25px;

        img {
            max-width: 20px;
        }
    }

}

.header-subtitle {
    font-size: 25px;
    line-height: 30px;
    max-width: 835px;

    @media screen and (max-width:1325px) {
        font-size: 22px;
        line-height: 27px;
        max-width: 85%;
    }

    @media screen and (max-width:940px) {
        font-size: 20px;
    }

    @media screen and (max-width:650px) {
        font-size: 14px;
    line-height: 17px;
    }
}
</style>