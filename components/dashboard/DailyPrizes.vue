<template>
    <DashboardCard title="Daily Tasks" icon="gift" class="scrollable">
        <div v-for="task in tasks" :key="task.id" class="item">
            <div class="main">
                <Column :xs="2" class="no-gutter">
                    <Devcoins :amount="task.amount" class="xs" />
                </Column>
                <Column :xs="10" class="no-gutter">
                    {{ task.message }}
                </Column>
            </div>
            <Button class="outline sm">{{ task.action }}</Button>
        </div>

        <div v-if="tasks.length === 0" class="item">
            <div class="main no-tasks">
                <Column :xs="15" class="no-gutter">
                    Currently no active daily tasks 😟
                </Column>
            </div>
        </div>
    </DashboardCard>
</template>

<script>
import DashboardCard from '@/components/DashboardCard';
import Devcoins from '@/components/Devcoins';

export default {
    name: 'DailyPrizes',
    components: { DashboardCard, Devcoins },

    data: () => ({
        tasks: [],
    }),
};
</script>

<style lang="scss" scoped>
@import 'utils.scss';

.item {
    @extend %flex-justify;
    padding: $grid-gutter-width;
    border-bottom: 1px solid $divider-color;
}

.main {
    width: 100%;
}

.no-tasks {
    text-align: center;
}
</style>
