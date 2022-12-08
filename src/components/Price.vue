<template>
    <section class="price__section">
        <div class="container">
            <div class="row">

                <Title :titleValue="title" :centerText="true"/>

                <div class="features__list">
                    <div class="features__list-item" v-for="(item, idx) in studyFeatures" :key="idx">
                        <img :src="require(`@/assets/${item.img}`)" alt="" class="features-icon">
                        <p class="features-text">{{ item.text }}</p>
                    </div>
                </div>

                <div class="price-table-box">
                    <Transition name="icon-fade">
                        <span class="phone-icon" v-if="windowSize < 880">
                            <i class="fas fa-mobile-alt"></i> <i class="far fa-long-arrow-right"></i>
                        </span>
                    </Transition>

                    <PriceTable/>
                </div>

                <div class="start-study__content">
                    <img :src="startStudyContent.img" alt="" class="start-study-img">

                    <p class="start-study-text">{{ startStudyContent.text }}</p>

                    <button class="start-btn orange-btn">Начать обучение <i class="fal fa-external-link"></i></button>
                </div>

            </div>
        </div>
    </section>

</template>

<script>
import Title from './Title.vue'
import PriceTable from './PriceTable.vue'

export default {
    name: 'Price',
    components: {
        Title,
        PriceTable
    },
    data() {
        return {
            title: 'Стоимость обучения',
            studyFeatures: [
                {
                    img: 'images/main/price/price-1.svg',
                    text: 'Весь курс разбит на несколько блоков. Оплата поэтапная вы платите только за тот блок, который сейчас проходите.'
                },
                {
                    img: 'images/main/price/price-2.svg',
                    text: 'Любой из блоков вы можете оплатить в рассрочку'
                },
                {
                    img: 'images/main/price/price-3.svg',
                    text: 'Если передумаете учиться, то возврат можно оформить в любой момент. Возвращаем деньги за 3 рабочих дня.'
                },
            ],
            windowSize: window.innerWidth,
            startStudyContent: {
                img: require('@/assets/images/main/price/megaphone.svg'),
                text: 'Все блоки проходятся строго по порядку. Пропустить какой-то блок или начать обучение с середины нельзя, даже если вы считаете, что уже знаете какую-то часть материала. Только так мы можем гарантировать, что вы получите все знания, предусмотренные учебной программой.'
            }
        }
    },
    mounted() {
        window.addEventListener('resize', () => this.windowSize = window.innerWidth)
    }
}

</script>

<style lang="scss" scoped>

.price__section {
    width: 100%;
    padding: 55px 0;

    .row {
        flex-direction: column;
        align-items: center;
        row-gap: 30px;
    }

    .features__list {
        width: 100%;
        display: flex;
        justify-content: space-between;
        align-items: center;
        row-gap: 20px;
        column-gap: 30px;

        .features__list-item {
            max-width: 400px;
            width: 100%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            gap: 15px;

            .features-icon {
                max-width: 60px;
                min-width: 45px;
                width: 100%;
            }

            .features-text {
                max-width: 300px;
                width: 100%;
                font-size: 15px;
                color: var(--main-blue);
                font-weight: 500;
                display: -webkit-box;
                -webkit-line-clamp: 4;
                -webkit-box-orient: vertical;
                overflow: hidden;
            }
        }
    }

    .price-table-box {
        width: 100%;
        overflow-x: auto;
        position: relative;

        .phone-icon {
            font-size: 30px;
            color: #C4C4C4;
            position: sticky;
            top: 0;
            left: 3%;
        }
    }

    .start-study__content {
        width: 100%;
        display: flex;
        align-items: center;
        justify-content: space-between;
        background: var(--main-white);
        border-radius: 30px;
        padding: 50px 45px;
        column-gap: 30px;
        row-gap: 20px;

        .start-study-img {
            max-width: 90px;
            width: 100%;
            min-width: 65px;
        }

        .start-btn {
            white-space: nowrap;
        }

        .start-study-text {
            max-width: 600px;
            width: 100%;
            font-size: 15px;
            color: var(--main-blue);
            font-weight: 500;
            display: -webkit-box;
            -webkit-line-clamp: 5;
            -webkit-box-orient: vertical;
            overflow: hidden; 
        }
    }
}

@media (max-width: 768px) {
    .features__list {
        flex-direction: column;
        justify-content: flex-start;

        .features__list-item {
            flex-direction: column;
            text-align: center;

            .features-text {
                max-width: 250px !important;
            }
        }
    }

    .start-study__content {
        flex-direction: column;
        justify-content: flex-start;
        text-align: center;
        padding: 40px 20px !important;

        .start-study-text {
            -webkit-line-clamp: 8 !important;
        }
    }
}

@media (max-width: 480px) {
    .start-study-img {
        max-width: 75px !important;
    }
}

.icon-fade-enter-active,
.icon-fade-leave-active {
  transition: opacity .4s ease;
}

.icon-fade-enter-from,
.icon-fade-leave-to {
  opacity: 0;
}


</style>