<template>
    <div class="SubScore">
        <div
            class="header"
            :class="{ noScore: (blueScore == null && redScore == null) || noScore }"
        >
            <span class="points team-blue">{{ blueScore }}</span>
            <h3 v-if="title">{{ title }}</h3>
            <span class="points team-red">{{ redScore }}</span>
        </div>

        <div class="main">
            <slot />
        </div>
    </div>
</template>

<script>
export default {
    name: 'SubScore',
    props: {
        noScore: {
            type: Boolean,
            required: false,
            default: false,
        },
        title: {
            type: String,
            default: '',
        },
        blueScore: {
            type: Number,
            required: false,
            default: 0,
        },
        redScore: {
            type: Number,
            required: false,
            default: 0,
        },
    },
};
</script>

<style lang="scss" scoped>
@import 'utils.scss';

.SubScore {
    padding: 0 $s-space;
    text-align: center;
}

.header {
    @extend %flex-justify;
    padding: $xs-space;
    margin: 0 auto $s-space;
    position: relative;

    h3 {
        @extend %absolute-center;
        display: block;
        text-transform: uppercase;
        font-family: $alt-font-face;
        font-weight: $font-weight-semibold;
        color: $text-color-secondary;
    }

    &.noScore {
        margin-bottom: 0;

        & > h3 {
            @include clear-position;
            width: 100%;
            padding: $xs-space 0;
        }

        & + .main {
            margin-bottom: $m-space;
            font-weight: $font-weight-regular;
        }

        .points {
            display: none;
        }
    }
}

.points {
    display: flex;
    align-items: center;
    font-size: 36px;
    font-weight: $font-weight-bold;

    &.aced:after {
        content: 'ACED';
        border: 1px solid $bonus-color;
        padding: $xxxs-space $xxs-space;
        margin: 0 $grid-gutter-width;
        font-weight: $font-weight-regular;
        font-size: $font-size-xs;
        color: $bonus-color;
    }

    &.team-blue {
        color: $brand-primary;
    }

    &.team-red {
        color: $brand-secondary;
    }
}
</style>
