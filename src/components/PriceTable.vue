<template>
    <table class="price-table">
        <thead>
            <tr>
                <th class="header-names" v-for="(name, idx) in headers" :key="idx">
                    {{ name.name }}
                </th>
            </tr>
        </thead>
        <tbody>
            <tr class="body-rows" v-for="(row, idd) in bodyInfos" :key="idd">
                <td class="block-name">{{ row.block }}</td>
                <td class="block-price">{{ row.price }}</td>
                <td class="block-period">{{ row.period }}</td>
            </tr>
        </tbody>
        <tfoot>
            <tr class="table-sum">
                <td class="sum-name">{{ sum.name }}</td>
                <td class="sum-num">{{ calcPrice }}</td>
                <td class="sum-period">{{ calcPeriod }}</td>
            </tr>
        </tfoot>
    </table>
</template>

<script>

export default {
    name: 'Price Table',
    data() {
        return {
            headers: [
                {
                    name: 'Блок'
                },
                {
                    name: 'Стоимость (₽)'
                },
                {
                    name: 'Расчетное время обучения (мес.) *'
                }
            ],
            bodyInfos: [
                {
                    block: 'Введение в программирование',
                    price: 'Бесплатно',
                    period: 0.5
                },
                {
                    block: 'Основы программирования на Python',
                    price: 9900,
                    period: 1
                },
                {
                    block: 'Python, продвинутый уровень',
                    price: 14900,
                    period: 2.5
                },
                {
                    block: 'Сети + фреймворк Flask',
                    price: 14900,
                    period: 2.5
                },
                {
                    block: 'Базы данных',
                    price: 14900,
                    period: 2
                },
                {
                    block: 'Фреймворк Django',
                    price: 14900,
                    period: 2
                },
                {
                    block: 'Разработка «боевого» проекта ',
                    price: 9900,
                    period: 1.5
                }
            ],
            sum: {
                name: 'Итого',
                price: 0,
                period: 0,
            }
        }
    },
    computed: {
        calcPrice() {
            let price = 0;
            this.bodyInfos.map(item => price += !isNaN(item.price) ? item.price : 0)

            this.sum.price = price;

            return price
        },
        calcPeriod() {
            let period = 0;
            this.bodyInfos.map(item => period += !isNaN(item.period) ? item.period : 0)

            this.sum.period = period;

            return period
        }
    }
}

</script>

<style lang="scss" scoped>

.price-table {
    width: 100%;
    min-width: 850px;
    text-align: left;
    background: var(--main-white);
    border-radius: 30px;
    padding: 35px 40px;
    border-spacing: 0;
    margin: 20px 0;

    .header-names {
        padding: 0 0 15px 15px;
        color: var(--main-light-blue);
        font-size: 15px;
    }

    .body-rows {
        &:nth-child(odd) {
            background: #F3F3F3;

            .block-name {
                border-top-left-radius: 10px;
                border-bottom-left-radius: 10px;
            }

            .block-period {
                border-top-right-radius: 10px;
                border-bottom-right-radius: 10px;
            }
        }

        .block-name {
            font-size: 17px;
            color: var(--main-blue);
        }

        .block-period {
            font-size: 17px;
            color: var(--main-blue);
        }

        td {
            padding: 15px 0 15px 15px;
        }
    }

    .table-sum {
        & > td {
            padding: 15px 0 0 15px;
            font-size: 20px;
            color: var(--main-blue);
            font-weight: 700;
        }
    }
}

</style>