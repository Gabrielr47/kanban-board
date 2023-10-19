<script setup lang="ts">
import draggable from 'vuedraggable'
import KanbanBodyColumns from './KanbanBodyColumns.vue'
import { type PropType } from 'vue'

defineProps({
  swimlanes: {
    type: Array,
    required: true
  },
  columns: {
    type: Array,
    required: true
  },
  groups: {
    type: Array as PropType<Record<string, any>[]>,
    required: true
  }
})
</script>

<template>
  <draggable
    :list="swimlanes"
    group="swimlanes"
    handle=".handle"
    item-key="key"
    ghost-class="ghost"
  >
    <template #item="{ element }">
      <div class="kanban-swimlane" :data-swimlane="element.key">
        <div class="kanban-swimlane-header">
          <p class="handle" @click="element.isClosed = !element.isClosed">{{ element.label }}</p>
          <div v-if="!element.isClosed">
            <KanbanBodyColumns :columns="columns" :swimlane="element" :groups="groups" />
          </div>
        </div>
      </div>
    </template>
  </draggable>
</template>
<style scoped>
.handle {
  cursor: pointer;
}
</style>
