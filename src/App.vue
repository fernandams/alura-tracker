<template>
  <main class = "columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <SidebarComponent />
    </div>
    <div class="column is-three-quarter">
      <FormComponent />
      <div class="list">
        <TaskComponent />
        <TaskComponent />
        <TaskComponent />
        <TaskComponent />
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import SidebarComponent from './components/SidebarComponent.vue';
import FormComponent from './components/FormComponent.vue';
import TaskComponent from './components/TaskComponent.vue';

export default defineComponent({
    name: 'App',
    components: {
    SidebarComponent,
    FormComponent,
    TaskComponent
}
});
</script>

<style>
.list {
  padding: 1.25rem;
}
</style>
