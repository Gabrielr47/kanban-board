<script setup lang="ts">
import { computed, PropType } from 'vue'
import draggable from 'vuedraggable'

const props = defineProps({
  column: {
    type: Object,
    required: true
  },
  swimlane: {
    type: Object,
    required: true
  },
  groups: {
    type: Array as PropType<Record<string, any>[]>,
    required: true
  }
})

const tickets = computed(() => {
  const group = props.groups.find((group) => {
    return (
      group.column.key === props.column.key &&
      (!props.swimlane || group.swimlane.key === props.swimlane.key)
    )
  })
  return group?.entries || []
})

</script>
<template>
  <div class="column">
    <draggable
      :list="tickets"
      class="kanban-body"
      group="tickets"
      item-key="key"
      ghost-class="ghost"
    >
      <template #item="{ element }">
          <div class="ticket">
            <strong>{{ element.id }}</strong>
            <p>{{ element.sys_subject }}</p>
          </div>
      </template>
    </draggable>
  </div>
</template>
<style scoped>
.ticket {
  background-color: #fff;
  border-radius: 0.25rem;
  box-shadow: 0 0.125rem 0.25rem rgba(0, 0, 0, 0.075);
  padding: 0.5rem;
  margin-bottom: 0.5rem;
}
</style>
