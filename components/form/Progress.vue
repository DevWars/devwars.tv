<template>
    <div>
        <div v-if="title" class="progress-header">
            <span class="progress-header__title">{{ title }}</span>
            <span class="progress-header__meta">{{ meta }}</span>
        </div>
        <div class="progress">
            <div class="bar" :style="{ width: progress }" :class="color" />
        </div>
    </div>
</template>

<script>
export default {
    name: 'Progress',
    props: {
        progress: {
            type: String,
            required: true,
        },
        title: {
            type: String,
            required: true,
        },
        meta: {
            type: String,
            default: '',
        },
        color: {
            type: String,
            default: '',
        },
    },
};
</script>

<style lang="scss" scoped>
@import 'utils.scss';

.progress {
    width: 100%;
    height: 5px;
    background-color: rgba(0, 0, 0, 0.6);
    overflow: hidden;
}

.bar {
    height: 100%;
    background-color: #fff;
    transition: all 0.4s cubic-bezier(0, 0.5, 0.35, 1.4);

    &.primary {
        background-color: $brand-primary;
    }
    &.secondary {
        background-color: $brand-secondary;
    }
    &.yellow {
        background-color: $bonus-color;
    }
}

.progress-header {
    @extend %flex-justify;
    margin-bottom: $xxs-space;

    &__title,
    &__meta {
        text-transform: uppercase;
        font-size: $font-size-sm;
    }
}
</style>
