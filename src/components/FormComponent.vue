<template>
    <div class="box form">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulário para criação de uma nova tarefa">
                <input
                    type="text"
                    class="input"
                    placeholder="Qual tarefa você deseja iniciar?"
                    v-model="description"
                />
            </div>
            <div class="column">
                <StopwatchComponent @stopwatchFinished="finishTask"/>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import StopwatchComponent from './StopwatchComponent.vue';

export default defineComponent({
    name: 'FormComponent',
    emits: ['whenSavingTask'],
    components: {
        StopwatchComponent
    },
    data () {
        return {
            description: ''
        }
    },
    methods: {
        finishTask (elapsedTime: number) : void {
            this.$emit('whenSavingTask', {
                durationInSeconds: elapsedTime,
                description: this.description
            });
            this.description = '';
        }
    }
});

</script>

<style>
.form {
    color: var(--primary-text);
    background-color: var(--primary-bg);
}
</style>
