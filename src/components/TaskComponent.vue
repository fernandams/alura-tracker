<template>
    <div class="box has-text-weight-bold">
        <div class="columns">
            <div class="column is-7">
                {{ task.description }}
            </div>
            <div class="column">
                <TimerComponent :timeInSeconds="task.durationInSeconds"/>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { PropType, defineComponent } from 'vue';
import TimerComponent from './TimerComponent.vue';
import ITask from '@/interfaces/ITask';

export default defineComponent({
    name: 'TaskComponent',
    components: {
        TimerComponent
    },
    props: {
        task: {
            type: Object as PropType<ITask>,
            required: true
        }
    }
});

</script>

<style scoped>
.box {
    background: #FAF0CA;
}
</style>
