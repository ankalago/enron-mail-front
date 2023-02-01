<template>
  <div class="text-sm text-gray-500">
    <div v-html="boldText(sanitizeText(itemSelected.content))">
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
    },
    textSearch: String
  },
  setup(props) {
    const sanitizeText = (text?: string) =>
        text?.replaceAll("\n", "<br />")

    const boldText = (text?: string) => {
      return props.textSearch ? text?.toLowerCase().replace(props.textSearch.toLowerCase(), `<span class="text-rose-500 font-bold">${props.textSearch}</span>`) : text
    }

    return {
      sanitizeText,
      boldText
    }
  }
})
</script>
