<template>
    <nav class="nav" :class="{'full': windowScrollY > 10}">
        <div class="container">
            <div class="row">

                <router-link to="/" class="logo"><span class="light-blue">R</span>X<span class="orange">F</span>R</router-link>

                <Transition name="fade">
                    <span class="list-bg" v-if="!mbListClosed" @click="mbListClosed = true"></span>
                </Transition>

                <ul class="nav__list" :class="{'mb-list': windowSize < 992, 'closed': windowSize < 992 && mbListClosed}">
                    <button class="mb-list-btn" v-if="windowSize < 992" @click="mbListClosed = true">
                        <i class="fal fa-times"></i>
                    </button>

                    <li class="nav__list-item" v-for="(link, idx) in links" :key="idx">
                        <router-link :to="link.url" class="nav__list-link">
                            {{ link.name }}
                        </router-link>
                    </li>

                    <li class="nav__list-item" v-if="windowSize < 992">
                        <button class="register-btn">Регистрация</button>
                    </li>
                </ul>

                <div class="modals-list">
                    <button class="register-btn" v-if="windowSize > 992">Регистрация</button>
                    <button class="sign-btn"><i class="fal fa-long-arrow-right"></i> Войти</button>

                    
                </div>

                <button class="mb-nav-btn" v-if="windowSize < 992" @click="mbListClosed = false">
                    <span class="btn-line"></span>
                    <span class="btn-line"></span>
                    <span class="btn-line"></span>
                </button>

            </div>
        </div>
    </nav>
</template>

<script>

export default {
    name: 'Nav',
    data() {
        return {
            logo: require('@/assets/icons/logo.svg'),
            links: [
                {
                    name: 'Чему вы научитесь',
                    url: ''
                },
                {
                    name: 'Процесс обучения',
                    url: ''
                },
                {
                    name: 'Стоимость',
                    url: ''
                },
                {
                    name: 'Контакты',
                    url: ''
                }
            ],
            windowSize: window.innerWidth,
            windowScrollY: window.scrollY,
            mbListClosed: true
        }
    },
    mounted() {
        window.addEventListener('resize', () => {
            this.windowSize = window.innerWidth
        })

        window.addEventListener('scroll', () => {
            this.windowScrollY = window.scrollY
        })
    }
}

</script>

<style lang="scss" scoped>

@mixin blueBtn {
    padding: 7px 15px;
    border-radius: 34px;
    background: var(--main-light-blue);
    color: var(--main-white);
    font-size: 15px;
    font-weight: 500;
    cursor: pointer;
    transition: .3s;

    &:hover {
        background: var(--main-orange);
    }
}

.nav {
    width: 100%;
    height: 45px;
    position: fixed;
    top: 10px;
    left: 0;
    transition: .3s;
    z-index: 2022;

    &::after {
        content: '';
        max-width: 1190px;
        width: 100%;
        height: 100%;
        display: block;
        background: var(--main-white);
        border-radius: 75px;
        z-index: -1;
        position: absolute;
        top: 0;
        left: 50%;
        transform: translateX(-50%);
        transition: .3s;
    }

    &.full {
        top: 0;

        &::after {
            max-width: 100%;
            border-radius: 0;
        }
    }

    .row {
        justify-content: space-between;
        align-items: center;
        column-gap: 15px;
    }

    &__list {
        max-width: max-content;
        width: 100%;
        display: flex;
        align-items: center;
        column-gap: 40px;

        &-link {
            font-size: 15px;
            font-weight: 500;
            color: var(--main-blue);
            transition: .3s;

            &:hover {
                color: var(--main-orange);
            }
        }

        &.mb-list {
            position: fixed;
            top: 1.5%;
            right: 1.5%;
            height: 97%;
            background: var(--main-white);
            flex-direction: column;
            row-gap: 10px;
            align-items: flex-start;
            border-radius: 20px;
            padding: 20px;
            padding-top: 15px;
            transition: .4s;

            .nav__list-link {
                font-size: 17px;
            }

            .register-btn {
                font-size: 17px !important;
            }

            &.closed {
                transform: translateX(120%);
            }
        }
    }

    .list-bg {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100vh;
        background: linear-gradient(0deg, rgba(34, 37, 59, 0.9), rgba(34, 37, 59, 0.9));
    }

    .mb-list-btn {
        background: transparent;
        margin-left: auto;
        border: 0;
        color: var(--copyright-gray);
        font-size: 30px;
        cursor: pointer;

        i {
            opacity: 0.7;
        }            
    }

    .logo {
        font-size: 28px;
        color: var(--main-blue);
        font-weight: 500;
        display: flex;
        align-items: center;

        .light-blue {
            color: var(--main-light-blue);
        }

        .orange {
            color: var(--main-orange);
        }
    }

    .modals-list {
        display: flex;
        column-gap: 15px;
        align-items: center;

        .sign-btn {
            border: 0;
            display: flex;
            align-items: center;
            column-gap: 5px;

            i {
                margin-top: 2.5px;
            }

            @include blueBtn();
        }
    }

    .register-btn {
        background: transparent;
        border: 0;
        cursor: pointer;
        color: var(--main-blue);
        font-weight: 500;
        font-size: 15px;
        transition: .4s;

        &:hover {
            color: var(--main-orange);
        }
    }

    .mb-nav-btn {
        width: 20px;
        background: transparent;
        border: 0;
        display: flex;
        flex-direction: column;
        align-items: center;
        row-gap: 4px;
        cursor: pointer;

        span {
            width: 100%;
            height: 2px;
            background: var(--main-orange);
        }
    }
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity .3s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

</style>