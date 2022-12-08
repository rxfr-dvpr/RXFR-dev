<template>
    <section class="how-works__section">
        <div class="container">
            <div class="row">

                <Title :titleValue="title" :centerText="true"/>

                <p class="how-works__text">{{ text }}</p>

                <div class="video-content">
                    <img :src="macbookImg" alt="" class="macbook-img">

                    <iframe width="560" height="315" src="https://www.youtube.com/embed/p059z-0JTFg" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
                </div>

                <div class="how-works__cards">

                    <div class="how-works__card" v-for="(card, idx) in cards" :key="idx">
                        <p class="card-num">0{{ idx + 1 }}</p>

                        <h3 class="how-works__card-title">{{ card.title }}</h3>

                        <p class="how-works__card-text">{{ card.text }}</p>
                    </div>

                </div>

                <div class="start-btn-box">
                    <button class="start-btn orange-btn"> Начать обучение <i class="fal fa-external-link"></i>
                    </button>

                    <p class="start-text">Попробуйте, первые уроки бесплатны, но нужно пройти тестирование</p>
                </div>
                
            </div>
        </div>
    </section>
</template>

<script>
import Title from './Title.vue'

export default {
    name: 'How Works',
    data() {
        return {
            title: 'Как происходит обучение на RXFR?',
            text: 'Обучение должно быть комфортным. Поэтому мы разработали собственную платформу для обучения программированию. На ней вы можете не только изучать теорию, но и запускать готовые примеры и даже писать свой собственный код.',
            macbookImg: require('@/assets/images/main/howWorks/macbook.svg'),
            cards: [
                {
                    title: 'Весь материал разбит на небольшие уроки',
                    text: 'Теория и практика подаются маленькими порциями. Так вам будет легче усваивать новые знания.'
                },
                {
                    title: 'Обучение через практику',
                    text: 'Всё, что вы узнали, вы тут же начинаете применять на практике. Вы сразу видите результаты своего труда.'
                },
                {
                    title: 'Нет ограничений по времени',
                    text: 'Можно совмещать учёбу с работой и другими делами. Не нужно выпрашивать академический отпуск, если пришлось сделать перерыв.'
                }
            ],
            bgShadow: require('@/assets/images/main/howWorks/bg-shadow.svg')
        }
    },
    components: {
        Title
    }
}

</script>

<style lang="scss" scoped>

.how-works__section {
    width: 100%;
    padding: 55px 0;

    .row {
        flex-direction: column;
        align-items: center;
        row-gap: 25px;
        text-align: center;
    }

    .how-works__text {
        max-width: 650px;
        font-size: 15px;
        color: var(--main-blue);
    }

    .video-content {
        max-width: 765px;
        width: 100%;
        position: relative;

        img {
            width: 100%;
            display: block;
        }

        iframe {
            width: 77%;
            height: 85%;
            position: absolute;
            top: 5%;
            left: 11.6%;
            border-radius: 8px;
        }
    }
    
    .how-works__cards {
        width: 100%;
        display: flex;
        justify-content: space-between;
        flex-wrap: wrap;
        text-align: start;
        gap: 25px;
        background: var(--main-white);
        box-shadow: 0px 81px 120px -77px rgba(34, 37, 59, 0.04);
        border-radius: 40px;
        padding: 40px 45px;

        .how-works__card {
            max-width: 270px;
            width: 100%;
            display: flex;
            flex-direction: column;
            row-gap: 15px;

            .card-num {
                font-size: calc(50px + 27 * (100vw / 1920));
                font-weight: 700;
                color: var(--main-light-blue);
            }

            &-title {
                font-size: calc(20px + 4 * (100vw / 1920));
            }

            &-text {
                font-size: calc(14px + 3 * (100vw / 1920));
                font-weight: 500;
                color: var(--main-blue);
                display: -webkit-box;
                -webkit-line-clamp: 4;
                -webkit-box-orient: vertical;
                overflow: hidden;
            }
        }
    }

    .start-btn-box {
        max-width: max-content;
        width: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-wrap: wrap;
        column-gap: 25px;
        row-gap: 15px;
        padding: 12px 14px;
        background: var(--main-white);
        border-radius: 110px;
        overflow: hidden;

        .start-text {
            max-width: 215px;
            width: 100%;
            font-size: 15px;
            font-weight: 600;
            color: var(--main-blue);
            text-align: start;
        }
    }
}

@media (min-width: 1920px) {
    .how-works__card {
        .card-num {
            font-size: 77px !important;
        }
        
        &-title {
            font-size: 24px !important;
        }

        &-text {
            font-size: 17px !important;
        }
    }
}

@media (max-width: 992px) {
    .how-works__cards {
        justify-content: center !important;
    }
}

@media (max-width: 786px) {
    
    .how-works__card {
        .card-num {
            font-size: calc(50px + (27 + 27 * 0.7) * ((100vw - 320px)/ 1920));
        }
        
        &-title {
            font-size: calc(20px + (4 + 4 * 0.7) * ((100vw - 320px)/ 1920));
        }

        &-text {
            font-size: calc(14px + (3 + 3 * 0.7) * ((100vw - 320px)/ 1920));
        }
    }
}

@media (max-width: 684px) {
    .how-works__cards {
        max-width: max-content;
        flex-direction: column;

        .how-works__card {
            row-gap: 8px !important;
        }
    }
}

@media (max-width: 512px) {
    .start-btn-box {
        max-width: 360px !important;
        flex-direction: column;
        border-radius: 30px !important;
        
        .start-text {
            text-align: center !important;
        }
    }
}

</style>