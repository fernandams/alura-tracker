<template>
    <div class="box">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulário para criação de uma nova tarefa">
                <input type="text" class="input" placeholder="Qual tarefa você deseja iniciar?">
            </div>
            <div class="column">
                <div class="is-flex is-align-items-center is-justify-content-space-between">
                    <TimerComponent :timeInSeconds="timeInSeconds"/>
                    <button class="button" @click="start">
                        <span class="icon">
                            <i class="fas fa-play"></i>
                        </span>
                        <span>play</span>
                    </button>
                    <button class="button" @click="finish">
                        <span class="icon">
                            <i class="fas fa-stop"></i>
                        </span>
                        <span>stop</span>
                    </button>
                </div>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import TimerComponent from './TimerComponent.vue';

export default defineComponent({
    name: 'FormComponent',
    data() {
        return {
            timeInSeconds: 0,
            timer: 0
        };
    },
    methods: {
        start() {
            this.timer = setInterval(() => {
                this.timeInSeconds += 1;
            }, 1000);
        },
        finish() {
            clearInterval(this.timer);
        }
    },
    components: { TimerComponent }
});

</script>