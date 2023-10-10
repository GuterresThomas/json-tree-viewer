<template>
  <div id="app">
    <JsonTreeView />
  </div>
</template>

<script>
import JsonTreeView from './components/jsonviewer.vue';

export default {
  components: {
    JsonTreeView,
  },
};
</script>


<style scoped>
  .app {
    display: flex;
    align-items: center;
    justify-content: center;
  }
</style>

