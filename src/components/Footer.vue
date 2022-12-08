<template>
    <footer class="footer">
        <div class="container">
            <div class="row">

                <div class="footer-right">
                    <router-link to="/" class="footer-logo"><span class="light-blue">R</span>X<span class="orange">F</span>R</router-link>

                    <div class="weblinks__list">
                        <a :href="weblink.url" class="web-link" target="_blank" v-for="(weblink, idx) in webLinks" :key="idx" v-html="weblink.icon"></a>
                    </div>
                </div>
                
                <ul class="footer__list">
                    <li class="footer__list-item" v-for="(link, idd) in footerLinks" :key="idd">
                        <router-link :to="link.url" class="footer__list-link">{{ link.name }}</router-link>
                    </li>
                </ul>

                <div class="footer__copyright">
                    <p class="copyright-text all-text">© {{ new Date().getFullYear() }} RXFR — Все права защищены</p>

                    <p class="agree-text all-text">Пользовательское соглашение</p>
                    <p class="policy-text all-text">Пользовательское соглашение</p>
                </div>

            </div>
        </div>
    </footer>
</template>

<script>

export default {
    name: 'Footer',
    data() {
        return {
            webLinks: [
                {
                    icon: '<i class="fab fa-instagram"></i>',
                    url: 'https://www.instagram.com/'
                },
                {
                    icon: '<i class="fab fa-vk"></i>',
                    url: 'https://vk.com/'
                },
                {
                    icon: '<i class="fab fa-facebook"></i>',
                    url: 'https://www.facebook.com/'
                },
                {
                    icon: '<i class="fab fa-youtube"></i>',
                    url: 'https://www.youtube.com/'
                }
            ],
            footerLinks: [
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
                },
                {
                    name: 'Регистрация',
                    url: ''
                }
            ]
        }
    }
}

</script>

<style lang="scss" scoped>

.footer {
    width: 100%;
    padding-top: 60px;
    background: var(--main-white);
    border-top-left-radius: 80px;
    border-top-right-radius: 80px;
    box-shadow: 0 0 35px rgba($color: #38BFF2, $alpha: .35);
    margin-top: 50px;

    .row {
        justify-content: space-between;
        flex-wrap: wrap;
        row-gap: 30px;
    }

    .footer-right {
        max-width: max-content;
        width: 100%;
        display: flex;
        flex-direction: column;
        row-gap: 30px;

        .footer-logo {
            font-size: 30px;
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

            &::after {
                content: 'Школа программирования';
                max-width: 150px;
                width: 100%;
                font-size: 14px;
                color: var(--copyright-gray);
                line-height: 100%;
                padding-left: 10px;
            }
        }

        .weblinks__list {
            max-width: max-content;
            width: 100%;
            display: flex;
            gap: 15px;
            align-items: center;

            .web-link {
                min-width: 35px;
                max-width: 35px;
                min-height: 35px;
                max-height: 35px;
                border-radius: 50%;
                background: var(--main-blue);
                color: var(--main-white);
                display: grid;
                place-items: center;
                font-size: 20px;
                padding-top: 1px;
                padding-left: 1px;
                transition: .3s;
                
                &:hover {
                    background: var(--main-orange);
                }
            }
        }
    }

    .footer__list {
        max-width: max-content;
        width: 100%;
        display: flex;
        flex-direction: column;
        row-gap: 15px;

        &-link {
            font-size: 15px;
            color: var(--main-blue);
            font-weight: 500;
            transition: .4s;

            &:hover {
                color: var(--main-orange);
            }
        }
    }

    .footer__copyright {
        width: 100%;
        display: flex;
        justify-content: space-between;
        align-items: center;
        flex-wrap: wrap;
        column-gap: 55px;
        row-gap: 20px;
        border-top: solid 1px #d8d8d8;
        padding: 25px 0;

        .all-text {
            font-size: 15px;
            color: var(--copyright-gray);
            font-weight: 500;
        }
    }
}

@media (max-width: 846px) {
    .footer {

        &-right {
            align-items: center;
            row-gap: 15px !important;
        }

        .row {
            flex-direction: column;
            justify-content: flex-start;
            align-items: center;
            text-align: center;
        }

        &__copyright {
            flex-direction: column;
            justify-content: flex-start;
            text-align: center;
        }
    }
}

</style>