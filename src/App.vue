<script setup lang="ts">
import { ref } from 'vue';
import kanban from './assets/kanban.json';
import KanbanHeaderColumns from './components/KanbanHeaderColumns.vue';
import KanbanSwimlanes from './components/KanbanSwimlanes.vue';

const headerColumns = ref(kanban?.data?.columns);
const swimlanes = ref(kanban?.data?.swimlanes);

console.log(kanban);
</script>

<template>
  <div class="kanban">
      <KanbanHeaderColumns :columns="headerColumns"/>
      <KanbanSwimlanes :swimlanes="swimlanes"/>
  </div>
</template>
