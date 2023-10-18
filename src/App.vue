<script setup lang="ts">
import kanban from './assets/kanban.json';
import KanbanHeaderColumns from './components/KanbanHeaderColumns.vue';

console.log(kanban);
</script>

<template>
  <div class="kanban">
      <KanbanHeaderColumns :columns="kanban?.data?.columns"/>
  </div>
</template>
