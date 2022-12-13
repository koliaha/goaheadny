<template>
    <div class="modal-wrapper">
        <div class="modal" v-if="!formActive">
            <div class="modal-close" @click="close"></div>
            <div class="modal-title">{{ data.title }}</div>
            <div class="modal-subtitle">
                {{ data.subtitle }}
            </div>
            <div class="modal-text">
                *Cсылка для активации подписки придёт тебе на почту в течение 2-х рабочих дней.
            </div>
            <button class="modal-link" @click="formActive = true">Выбрать этот подарок</button>
        </div>
        <div class="modal modal-form" v-else-if="!sended">
            <div class="modal-close" @click="close"></div>
            <div class="modal-title-form">Заполни данные <br />
                для получения подарка</div>
            <form action="" class="form" @submit.prevent="sendData">
                <div class="input-form">
                    <input type="text" v-model="nameInput" placeholder="Имя Фамилия" required>
                </div>
                <div class="input-form">
                    <input type="tel" v-model="phoneInput" placeholder="Номер телефон" required>
                </div>
                <div class="input-form">
                    <input type="email" v-model="mailInput" placeholder="Почта" required>
                </div>

                <p class="form-text">* — поля, обязательные для заполнения</p>
                <button type="submit" :disabled="isLoading" class="form-btn">Получить подарок</button>
                <p class="form-text">Нажимая кнопку «Получить подарок», вы даёте свое согласие на <a
                        href="https://gomobile.ru/uploads/origin/files/1/politika_obrabotki_personalnyh_dannyh.pdf"
                        target="_blank">обработку
                        персональных
                        данных</a> и соглашаетесь с <a
                        href="https://gomobile.ru/uploads/origin/files/1/politika_obrabotki_personalnyh_dannyh.pdf"
                        target="_blank"> политикой обработки персональных данных</a></p>
            </form>
        </div>
        <div class="modal greet" v-else>
            <div class="modal-close" @click="close"></div>
            <div class="modal-title">Ура</div>
            <div class="modal-subtitle">
                Спасибо за участие!
            </div>

            <button class="modal-link" @click="close">Закрыть</button>
        </div>
    </div>
</template>
<script>
export default {
    props: ["data"],
    data() {
        return {
            formActive: false,
            url: 'https://script.google.com/macros/s/AKfycbxSOAd8Js1JuOBQRdNstHr9QmaobLOTBiZQxRpB8QY6v8dZkRbVh0HqYsrjXJBPEyo0WQ/exec',
            nameInput: '',
            phoneInput: '',
            mailInput: '',
            sended: false,
            isLoading: false
        }
    },
    methods: {
        close() {
            this.$emit("close")
        },
        async sendData() {
            this.isLoading = true
            const present = `Выбран подарок ${this.data.title}`
            const data = [this.nameInput, this.phoneInput, this.mailInput, present]
            await fetch(this.url, {
                method: "POST",
                mode: "no-cors",
                headers: {
                    "Content-Type": "application/json",
                },
                body: JSON.stringify(data),
            })
                .then((response) => response.text())
                .then((el) => {
                    console.log(el);
                    this.sended = true
                    this.isLoading = false
                })
                .catch((error) => console.log("error", error));
        }
    }
}
</script>
<style lang="scss">
.modal-wrapper {}

.modal {
    background: #131212;
    border: 1px solid #FF7323;
    border-radius: 35px;
    padding: 70px 57px;
    position: fixed;
    left: 20%;
    top: 50%;
    z-index: 100;
    transform: translateY(-50%);
    max-width: 520px;
    width: 100%;

    @media screen and (max-width:1125px) {
        left: 50%;
        transform: translate(-50%, -50%);
    }

    @media screen and (max-width:725px) {
        max-width: 85%;
    }

    @media screen and (max-width:650px) {
        padding: 35px 25px;
    }
}

.greet {
    text-align: center;
}

.modal-close {
    cursor: pointer;
    position: absolute;
    right: 32px;
    top: 32px;
    width: 32px;
    height: 32px;
    transition: 0.4s;

    &:before,
    &:after {
        position: absolute;
        left: 15px;
        content: " ";
        height: 33px;
        width: 2px;
        background-color: #FF7323;
    }

    &:hover {
        opacity: 1;
    }

    &:before {
        transform: rotate(45deg);
    }

    &:after {
        transform: rotate(-45deg);
    }



}

.modal-title {
    font-weight: 700;
    font-size: 45px;
    line-height: 54px;
    margin-bottom: 20px;

    @media screen and (max-width:450px) {
        font-size: 33px;
        line-height: 40px;
    }
}

.modal-subtitle {
    font-weight: 300;
    font-size: 30px;
    line-height: 36px;
    margin-bottom: 52px;

    @media screen and (max-width:450px) {
        font-size: 21px;
        line-height: 25px;
        margin-bottom: 25px;
    }
}

.modal-text {
    font-weight: 300;
    font-size: 16px;
    line-height: 19px;
    opacity: 0.5;
    margin-bottom: 20px;

    @media screen and (max-width:450px) {
        font-size: 12px;
        line-height: 13px;
        margin-bottom: 15px;
    }
}

.modal-link {
    cursor: pointer;
    outline: none;
    background: #FF7323;
    border-radius: 15px;
    color: white;
    max-width: 360px;
    width: 100%;
    text-align: center;
    font-weight: 500;
    font-size: 20px;
    line-height: 23px;
    padding: 22px 0;
    transition: 0.4s;

    &:hover {
        opacity: 0.8;
    }

    @media screen and (max-width:450px) {
        font-size: 17px;
        line-height: 13px;
        padding: 15px 0;
    }
}

.modal-form {
    border: 1px solid #FFFFFF;

    .modal-close {

        &:before,
        &:after {
            background-color: #FFFFFF;
        }
    }
}

.modal-title-form {
    font-size: 25px;
    line-height: 30px;
    text-align: center;
    margin-bottom: 37px;
}

.form {
    display: flex;
    flex-direction: column;

    .input-form {
        input {
            width: 100%;
            border: 1px solid rgba(255, 255, 255, 0.3);
            border-radius: 10px;
            background: none;
            margin-bottom: 21px;
            padding: 16px 26px;
            color: white;
        }

        padding-right: 26px;
        position: relative;

        &::after {
            position: absolute;
            content: '*';
            font-weight: 400;
            font-size: 30px;
            color: white;
            right: 0;
            top: 50%;
            transform: translateY(-50%);
        }
    }

    .form-text {
        font-weight: 300;
        font-size: 10px;
        line-height: 14px;
        color: rgba(255, 255, 255, 0.6);
        a{
            text-decoration: underline;
        }
    }

    .form-btn {
        cursor: pointer;
        outline: none;
        background: #ffffff;
        border-radius: 15px;
        color: rgb(0, 0, 0);
        width: 100%;
        text-align: center;
        font-weight: 500;
        font-size: 20px;
        line-height: 23px;
        padding: 22px 0;
        transition: 0.4s;
        margin: 43px 0 16px;

        &:hover {
            opacity: 0.8;
        }
    }
}
</style>