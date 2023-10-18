<script setup lang="ts">
import draggable from 'vuedraggable'

defineProps({
  swimlanes: {
    type: Array,
    required: true
  },
});

</script>

<template>
  <draggable
    :list="swimlanes"
    group="people"
    item-key="key"
    ghost-class="ghost"
  >
    <template #item="{ element }">
      <div class="kanban-swimlane" :data-swimlane="element.key">
        <div class="kanban-swimlane-header">
          <p  class="handle" @click="element.isClosed = !element.isClosed">{{ element.label }}</p>
          <div v-if="!element.isClosed">
            Pipoca
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