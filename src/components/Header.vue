<template>
  <header class="header">
    <div class="container">
        <div class="row">

            <div class="header__content">
                <h1 class="header__content-title" v-html="headerContent.title"></h1>
                <span class="line-gap"></span>

                <p class="header__content-text">{{ headerContent.text }}</p>
                
                <button class="test-btn orange-btn">Пройти тестирование <i class="fal fa-external-link"></i></button>
            </div>

            <img :src="headerImg" alt="" class="header__img">
        </div>
    </div>
  </header>
</template>

<script>

export default {
    name: 'Header',
    data() {
        return {
            headerImg: require('@/assets/images/header/header-img.svg'),
            headerContent: {
                title: 'Школа <span class="bracket">{ <code class="italic">программирования</code> }</span> для тех, кому нужны реальные навыки, а не просто сертификат',
                text: 'Пройдите тестирование, чтобы получить доступ к бесплатным вводным урокам'
            }
        }
    }
}

</script>

<style lang="scss" scoped>

.header {
    width: 100%;
    padding: 135px 0 60px;

    .row  {
        justify-content: space-between;
        align-items: center;
        column-gap: 20px;
        row-gap: 40px;
        flex-wrap: nowrap;
    }

    .header__content {
        max-width: 650px;
        width: 100%;
        display: flex;
        flex-direction: column;
        row-gap: 20px;

        &-title {
            font-size: calc(22px + 24 * (100vw / 1920));
            color: var(--main-blue);
            font-weight: 600;
            line-height: 100%;
        }

        .line-gap {
            max-width: 365px;
            width: 100%;
            height: 1px;
            background: #DEDEDE;
        }

        &-text {
            max-width: 365px;
            width: 100%;
            font-size: calc(14px + 3 * (100vw / 1920));
            color: var(--main-blue);
            font-weight: 500;
        }
    }

    .header__img {
        max-width: 390px;
        width: 100%;
    }
}

@media (max-width: 992px) {
    .header {
        padding: 90px 0 40px;
        
        .row {
            flex-direction: column;
            justify-content: flex-start;
        }

        .header__content {
            flex-direction: column;
            align-items: center;
            text-align: center;
        }
    }
}

@media (max-width: 668px) {
    .header {
        padding: 75px 0 30px;

        &__content {
            &-title {
                font-size: calc(22px + (24 + 24 * 0.7) * ((100vw - 320px)/ 1920));
            }
    
            &-text {
                font-size: calc(14px + (3 + 3 * 0.7) * ((100vw - 320px)/ 1920));
            }
        }

        &__img {
            padding: 0 20px;
        }
    }

}

@media (min-width: 1920px) {
    .header {
        &__content {
            &-title {
                font-size: 46px !important;
            }
    
            &-text {
                font-size: 17px !important;
            }
        }
    }
}

</style>