<template>
  <main class = "columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <SidebarComponent />
    </div>
    <div class="column is-three-quarter">
      <FormComponent />
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import SidebarComponent from './components/SidebarComponent.vue';
import FormComponent from './components/FormComponent.vue';

export default defineComponent({
    name: 'App',
    components: {
    SidebarComponent,
    FormComponent,
}
});
</script>

<style>

</style>
