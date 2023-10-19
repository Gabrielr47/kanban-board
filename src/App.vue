<script setup lang="ts">
import { ref } from 'vue';
import kanban from './assets/kanban.json';
import KanbanHeaderColumns from './components/KanbanHeaderColumns.vue';
import KanbanSwimlanes from './components/KanbanSwimlanes.vue';

const headerColumns = ref(kanban?.data?.columns);
const swimlanes = ref(kanban?.data?.swimlanes);
const groups = ref(kanban?.data?.groups);

</script>

<template>
  <div class="kanban">
      <KanbanHeaderColumns :columns="headerColumns"/>
      <KanbanSwimlanes :swimlanes="swimlanes" :columns="headerColumns" :groups="groups"/>
  </div>
</template>
