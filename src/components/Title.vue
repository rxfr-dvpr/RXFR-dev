<template>
  <h2 class="unique-title" :class="{'centered': centerText}">{{ titleValue }}</h2>
</template>

<script>

export default {
    name: 'Unique Title',
    props: {
        titleValue: {
            type: String,
            required: true,
            default: 'title'
        },
        centerText: {
            type: Boolean,
            default: false,
        }
    }
}

</script>

<style lang="scss" scoped>

.unique-title {
    max-width: 650px;
    width: 100%;
    font-size: calc(22px + 24 * (100vw / 1920));
    color: var(--main-blue);
    font-weight: 600;
    line-height: 100%;

    &.centered {
        text-align: center;
    }
}

@media (max-width: 668px) {
    .unique-title {
        font-size: calc(22px + (24 + 24 * 0.7) * ((100vw - 320px)/ 1920));
    }
}

@media (min-width: 1920px) {
    .unique-title {
        font-size: 46px;
    }
}

</style>