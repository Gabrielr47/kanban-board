<script setup lang="ts">
import { ref } from 'vue';
import draggable from 'vuedraggable'

const props = defineProps({
  columns: {
    type: Array,
    required: true
  },
});

const columnsLength = ref(props.columns?.length);

</script>
<template>
  <draggable
    :list="columns"
    class="columns"
    group="header-columns"
    item-key="key"
    ghost-class="ghost"
  >
    <template #item="{ element }">
      <div class="column" :data-header-column="element.key">
        <div class="kanban-header">
          <p>{{ element.label }}</p>
        </div>
      </div>
    </template>
  </draggable>
</template>
<style scoped>
.columns {
  display: grid;
  grid-template-columns: repeat(v-bind(columnsLength), minmax(12rem, 20rem));
  gap: 6px;
}
</style>
```
