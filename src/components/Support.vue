<template>
    <section class="support__section">
        <div class="container">
            <div class="row">
            
            <div class="support__content all-content">
                <div class="support-img-box all-img-box">
                    <img :src="supportContent.img" alt="" class="support-img all-img">
                </div>

                <div class="support__content-desc all-desc">
                    <h3 class="support__title all-title">{{ supportContent.title }}</h3>
                    <p class="support__text all-text">{{ supportContent.text }}</p>
                </div>
            </div>

            <div class="method__content all-content">
                <div class="method__content-desc all-desc">
                    <h3 class="method all-title">{{ methodContent.title }}</h3>
                    <p class="method__text all-text">{{ methodContent.text }}</p>
                </div>

                <div class="method-img-box all-img-box">
                    <img :src="methodContent.img" alt="" class="method-img all-img">
                </div>
            </div>


            </div>
        </div>
    </section>
</template>

<script>

export default {
    name: 'Support Section',
    data() {
        return {
            supportContent: {
                img: require('@/assets/images/main/support/support-1.svg'),
                title: 'Помощь и поддержка',
                text: 'Если в процессе обучения возникнут сложности, вы всегда сможете задать вопрос своему наставнику. Раз в несколько уроков вы будете получать большое задание, которое нужно будет сдавать на проверку код-ревьюеру. Он внимательно изучит ваш код, найдет ошибки и поможет вам стать лучше.'
            },
            methodContent: {
                img: require('@/assets/images/main/support/support-2.svg'),
                title: 'Методика обучения',
                text: 'Весь учебный материал структурирован по принципу «спирального обучения». Сначала вы получаете базовые знания, а затем на каждом витке спирали углубляетесь в изученные темы, доводя их понимание до совершенства. Такой подход упрощает обучение и гарантирует, что вы не пропустите ничего важного.'

            }
        }
    }
}

</script>

<style lang="scss" scoped>

@mixin bgBlue() {
    background: #EAF2F5;
    border-radius: 40px;
}

.support__section {
    width: 100%;
    border-radius: 80px;
    background: var(--main-white);
    box-shadow: 0 0 35px rgba($color: #38BFF2, $alpha: .35);
    padding: 55px 0;

    .row {
        flex-direction: column;
        row-gap: 30px;
    }

    .all-content {
        width: 100%;
        display: flex;
        justify-content: space-between;
        gap: 30px;

        .all-img-box {
            max-width: 400px;
            width: 100%;
            @include bgBlue();
            display: grid;
            place-items: center;
            padding: 40px 65px;

            .all-img {
                width: 100%;
                object-fit: cover;
            }
        }

        .all-desc {
            max-width: 730px;
            width: 100%;
            display: flex;
            flex-direction: column;
            row-gap: 15px;
            padding: 50px 100px;
            justify-content: center;
            @include bgBlue();

            .all-title {
                font-size: calc(20px + 12 * (100vw / 1920));
                font-weight: 600;
            }

            .all-text {
                font-size: 16px;
                font-weight: 500;
                color: var(--main-blue);
            }
        }
    }
}

@media (min-width: 1920px) {
    .all-title {
        font-size: 32px !important; 
    }
}

@media (max-width: 992px) {
    .all-img-box {
        padding: 30px 40px !important;
    }

    .all-desc {
        padding: 40px 60px !important;
    }
}

@media (max-width: 850px) {
    .all-content {
        flex-direction: column;
        align-items: center;
        row-gap: 15px !important;
    }
    
    .method-img-box {
        order: -1;
    }

    .all-desc {
        max-width: 400px !important;
        padding: 30px 25px !important;
    }
}

@media (max-width: 768px) {
    .all-title {
        font-size: calc(20px + (12 + 12 * 0.7) * ((100vw - 320px)/ 1920)) !important;
    }
}

</style>