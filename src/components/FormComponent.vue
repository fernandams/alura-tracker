<template>
    <div class="box">
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
            console.log('Tempo da tarefa: ', elapsedTime);
            console.log('Descrição da tarefa: ', this.description);
            this.description = '';
        }
    }
});

</script>