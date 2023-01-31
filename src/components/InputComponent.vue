<template>
  <input type="text"
         class="block w-full flex-1 border-gray-300 focus:border-indigo-500 focus:ring-indigo-500 sm:text-sm"
         :placeholder="placeHolder" @input="handleChange"
         :class="{ 'rounded-l-md': customClass === 'rounded-l-md', 'rounded-r-md': customClass === 'rounded-r-md', 'rounded-md': customClass === 'rounded-md', 'rounded-none': customClass === 'rounded-none' }"/>
</template>
<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'InputComponent',
  emits: ['customChange'],
  props: {
    placeHolder: String,
    customClass: String
  },
  methods: {
    handleChange(event: any) {
      this.$emit("customChange", event.target.value)
    }
  }
})
</script>
