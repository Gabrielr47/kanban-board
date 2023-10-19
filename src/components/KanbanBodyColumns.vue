<script setup lang="ts">
import { ref } from 'vue';
import KanbanTicket from './KanbanTicket.vue'

const props = defineProps({
  columns: {
    type: Array,
    required: true
  },
  swimlane: {
    type: Object,
    required: true
  },
  groups: {
    type: Array,
    required: true
  }
})

const columnsLength = ref(props.columns?.length);

</script>
<template>
  <div class="columns">
    <template v-for="column in columns" :key="column.key">
      <KanbanTicket :column="column" :swimlane="swimlane" :groups="groups" />
    </template>
  </div>
</template>
<style scoped>
.columns {
  display: grid;
  grid-template-columns: repeat(v-bind(columnsLength), minmax(12rem, 20rem));
  gap: 6px;
}
</style>
