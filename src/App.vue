<template>
  <main class = "columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <SidebarComponent />
    </div>
    <div class="column is-three-quarter">
      <FormComponent @whenSavingTask="saveTask" />
      <div class="list">
        <TaskComponent v-for="(task, index) in tasks" :key="index" :task="task"/>
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

export default defineComponent({
  name: 'App',
  components: {
    SidebarComponent,
    FormComponent,
    TaskComponent
  },
  data () {
    return {
      tasks: [] as ITask[]
    }
  },
  methods: {
    saveTask(task: ITask) {
      this.tasks.push(task);
    }
  }

});
</script>

<style>
.list {
  padding: 1.25rem;
}
</style>
