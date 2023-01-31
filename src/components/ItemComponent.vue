<template>
  <div class="text-sm text-gray-500">
    <div v-html="sanitizeText(itemSelected.content)">
    </div>
  </div>
</template>
<script lang="ts">
import { defineComponent } from 'vue';
import type { PropType } from 'vue'
import { ItemSelectedType } from '../entities/item';

export default defineComponent({
  name: 'ItemComponent',
  props: {
    itemSelected: {
      type: Object as PropType<ItemSelectedType>,
      required: true
    }
  },
  setup() {
    const sanitizeText = (text?: string) =>
        text?.replaceAll("\n", "<br />")

    return {
      sanitizeText
    }
  }
})
</script>
