
import TimerComponent from './TimerComponent.vue';
<template>
    <div class="box has-text-weight-bold">
        <div class="columns">
            <div class="column is-7">
                Descrição da tarefa
            </div>
            <div class="column">
                <TimerComponent :timeInSeconds="15"/>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import TimerComponent from './TimerComponent.vue';

export default defineComponent({
    name: 'TaskComponent',
    components: { TimerComponent }
});

</script>

<style scoped>
.box {
    background: #FAF0CA;
}
</style>