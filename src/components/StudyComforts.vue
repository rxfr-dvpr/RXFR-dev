<template>
    <section class="study-comforts__section">
        <div class="container">
            <div class="row">

                <Title :titleValue="title" :centerText="true"/>

                <div class="comforts__list">

                    <div class="comfort-card" v-for="(card, idx) in comfortCards" :key="idx">
                        <img :src="card.img" alt="" class="comfort-card__img">

                        <h2 class="comfort-card__title">{{ card.title }}</h2>

                        <p class="comfort-card__text">{{ card.text }}</p>
                    </div>

                </div>

            </div>
        </div>
    </section>
</template>

<script>
import Title from './Title.vue'

export default {
    name: 'Study Comforts',
    data() {
        return {
            title: 'Обучение в RXFR – это удобно и результативно',
            comfortCards: [
                {
                    title: 'Огромное количество практики',
                    text: 'Более 500 самостоятельных заданий и 20 полноценных больших проектов',
                    img: require('@/assets/images/main/studyComforts/comfort-1.svg')
                },
                {
                    title: 'Современные методики обучения',
                    text: 'Спиральное обучение: погружаемся в материал постепенно, виток за витком',
                    img: require('@/assets/images/main/studyComforts/comfort-2.svg')
                },
                {
                    title: 'Простое и понятное изложение',
                    text: 'Вместо заумных терминов – примеры из реального мира',
                    img: require('@/assets/images/main/studyComforts/comfort-3.svg')
                },
                {
                    title: 'Гибкий график занятий',
                    text: 'Учитесь в любое время в удобном для вас темпе',
                    img: require('@/assets/images/main/studyComforts/comfort-4.svg')
                },
                {
                    title: 'Прямая связь с опытными программистами',
                    text: 'Задавайте вопросы и отправляйте свой код на проверку',
                    img: require('@/assets/images/main/studyComforts/comfort-5.svg')
                },
                {
                    title: 'Оплата небольшими частями',
                    text: 'Платите только за тот материал, который сейчас изучаете, а не за весь курс сразу',
                    img: require('@/assets/images/main/studyComforts/comfort-6.svg')
                },
                {
                    title: 'Быстрый и легкий возврат',
                    text: 'Если передумаете учиться – вернем деньги за 3 рабочих дня',
                    img: require('@/assets/images/main/studyComforts/comfort-7.svg')
                }
            ]
        }
    },
    components: {
        Title
    }
}

</script>

<style lang="scss" scoped>

.study-comforts__section {
    width: 100%;
    padding: 55px 0;
    background: var(--main-white);
    border-bottom-right-radius: 80px;
    border-bottom-left-radius: 80px;
    box-shadow: 0 25px 30px rgba($color: #38BFF2, $alpha: .15);

    .row {
        flex-direction: column;
        align-items: center;
        row-gap: 35px;
    }

    .comforts__list {
        width: 100%;
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
        gap: 20px;

        .comfort-card {
            max-width: 270px;
            width: 100%;
            display: flex;
            flex-direction: column;
            align-items: center;
            text-align: center;
            row-gap: 10px;
            padding: 30px 10px;
            padding: 50px;
            background: #EAF2F5;
            border-radius: 30px;
            
            &__title {
                font-size: 16px;
                color: var(--main-blue);
                font-weight: 600;
                display: -webkit-box;
                -webkit-line-clamp: 2;
                -webkit-box-orient: vertical;
                overflow: hidden;
            }

            &__text {
                font-size: 13px;
                color: var(--main-blue);
                display: -webkit-box;
                -webkit-line-clamp: 4;
                -webkit-box-orient: vertical;
                overflow: hidden;
            }
        }
    }
}

</style>