<template>
  <main class = "columns is-gapless is-multiline" :class="{ 'dark-mode': activeDarkMode}">
    <div class="column is-one-quarter">
      <SidebarComponent @whenChangedTheme="changeTheme"/>
    </div>
    <div class="column is-three-quarter content">
      <FormComponent @whenSavingTask="saveTask" />
      <div class="list">
        <TaskComponent v-for="(task, index) in tasks" :key="index" :task="task"/>
        <BoxComponent v-if="isListEmpty">
          Você não está muito produtivo hoje :(
        </BoxComponent>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import SidebarComponent from './components/SidebarComponent.vue';
import FormComponent from './components/FormComponent.vue';
import TaskComponent from './components/TaskComponent.vue';
import ITask from './interfaces/ITask';
import BoxComponent from './components/BoxComponent.vue';

export default defineComponent({
  name: 'App',
  components: {
    SidebarComponent,
    FormComponent,
    TaskComponent,
    BoxComponent
},
  data () {
    return {
      tasks: [] as ITask[],
      activeDarkMode: false
    }
  },
  computed: {
    isListEmpty () : boolean {
      return this.tasks.length === 0;
    }
  },
  methods: {
    saveTask(task: ITask) {
      this.tasks.push(task);
    },
    changeTheme(activeDarkMode: boolean) {
      this.activeDarkMode = activeDarkMode;
    }
  }

});
</script>

<style>
.list {
  padding: 1.25rem;
}
main {
  --primary-bg:#fff;
  --primary-text: #000;
}
main.dark-mode {
  --primary-bg: #2b2d42;;
  --primary-text: #ddd;
}
.content {
  background-color: var(--primary-bg);
}
</style>
