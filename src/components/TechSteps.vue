<template>
  <section class="tech-steps__section">
    <div class="container">
        <div class="row">

            <Title :titleValue="techContent.title" :centerText="true"/>

            <div class="tech-steps__content">
                <img :src="techImg" alt="" class="tech-img" v-if="windowSize > 768">

                <div class="tech-steps__desc">

                    <div class="techs__list">
                        <span class="techs-name" v-for="(tech, idx) in techs" :key="idx" :style="`background: ${tech.bgColor}`">
                            {{ tech.name }}
                        </span>
                    </div>

                    <p class="tech-steps__text" v-if="windowSize > 850">
                        {{ techContent.text }}
                    </p>
                </div>
            </div>

        </div>
    </div>
  </section>
</template>

<script>
import Title from './Title.vue'

export default {
    name: 'Tech Steps',
    data() {
        return {
            techImg: require('@/assets/images/main/techSteps/tech-img.svg'),
            techContent: {
                title: 'Какие технологии вы изучите:',
                text: 'Это необходимый минимум для современного backend-разработчика',
            },
            techs: [
                {
                    name: 'Язык программирования Python',
                    bgColor: '#5096FF'
                },
                {
                    name: 'Сети',
                    bgColor: '#FFB359'
                },
                {
                    name: 'Базы данных',
                    bgColor: '#FF6F50'
                },
                {
                    name: 'Фреймворки Flask и Django',
                    bgColor: '#4BD071'
                },
                {
                    name: 'Отладка и тестирование',
                    bgColor: '#50C0FF'
                },
                {
                    name: 'Docker',
                    bgColor: '#4B77B9'
                },
                {
                    name: 'Git',
                    bgColor: '#AF93FF'
                }
            ],
            windowSize: window.innerWidth
        }
    },
    components: {
        Title
    },
    mounted() {
        window.addEventListener('resize', () => {
            this.windowSize = window.innerWidth
        })
    }
}

</script>

<style lang="scss" scoped>

.tech-steps__section {
    width: 100%;
    padding: 40px 0;

    .row {
        flex-direction: column;
        row-gap: 35px;
        align-items: center;
    }

    .tech-steps__content {
        width: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
        column-gap: 50px;
        row-gap: 20px;
        background: #EAF2F5;
        border-radius: 48px;
        padding: 40px 15px 0 15px;

        .tech-img {
            max-width: 405px;
            width: 100%;
        }

        .tech-steps__desc {
            max-width: 465px;
            width: 100%;
            display: flex;
            flex-direction: column;
            row-gap: 25px;

            .techs__list {
                width: 100%;
                display: flex;
                flex-wrap: wrap;
                gap: 10px;

                .techs-name {
                    font-size: calc(15px + 2 * (100vw / 1920));
                    color: var(--main-white);
                    font-weight: 500;
                    border-radius: 44px;
                    padding: 10px 15px;
                    text-align: center;
                }
            }

            .tech-steps__text {
                font-size: 17px;
                font-weight: 600;
                color: var(--main-blue);
            }
        }
    }
}

@media (max-width: 850px) {

    .tech-steps__content {
        flex-direction: column;
        padding: 15px !important;

        .techs__list {
            justify-content: center;
        }
    }
}

@media (max-width: 768px) {
    .row {
        align-items: center;
    }

    .tech-steps__content {
        max-width: max-content;
    }

    .techs-name {
        font-size: calc(15px + (2 + 2 * 0.7) * ((100vw - 320px)/ 1920));
    }
}

</style>