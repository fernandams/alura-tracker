<template>
    <section class="is-flex is-align-items-center is-justify-content-space-between">
        <TimerComponent :timeInSeconds="timeInSeconds" />
        <ButtonComponent @clicked="start" icon="fas fa-play" text="play" :disabled="isTimerRunning"/>
        <ButtonComponent @clicked="finish" icon="fas fa-stop" text="stop" :disabled="!isTimerRunning"/>
    </section>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import TimerComponent from './TimerComponent.vue';
import ButtonComponent from './ButtonComponent.vue';

export default defineComponent({
    name: 'StopwatchComponent',
    emits: ['stopwatchFinished'],
    data() {
        return {
            timeInSeconds: 0,
            timer: 0,
            isTimerRunning: false
        };
    },
    methods: {
        start() {
            this.isTimerRunning = true;
            this.timer = setInterval(() => {
                this.timeInSeconds += 1;
            }, 1000);
        },
        finish() {
            this.isTimerRunning = false;
            clearInterval(this.timer);
            this.$emit('stopwatchFinished', this.timeInSeconds);
            this.timeInSeconds = 0;
        }
    },
    components: {
        TimerComponent,
        ButtonComponent
    }
});

</script>