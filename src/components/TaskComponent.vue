<template>
    <BoxComponent>
        <div class="columns">
            <div class="column is-7">
                {{ task.description || 'Tarefa sem descrição'}}
            </div>
            <div class="column">
                <TimerComponent :timeInSeconds="task.durationInSeconds"/>
            </div>
        </div>
    </BoxComponent>
</template>

<script lang="ts">
import { PropType, defineComponent } from 'vue';
import TimerComponent from './TimerComponent.vue';
import ITask from '@/interfaces/ITask';
import BoxComponent from './BoxComponent.vue';

export default defineComponent({
    name: 'TaskComponent',
    components: {
        TimerComponent,
        BoxComponent
},
    props: {
        task: {
            type: Object as PropType<ITask>,
            required: true
        }
    }
});

</script>
