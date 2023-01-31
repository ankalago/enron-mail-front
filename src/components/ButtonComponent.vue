<template>
  <button
      class="inline-flex justify-center rounded-r-md border border-l-0 border-transparent bg-rose-600 py-2 px-4 text-sm font-medium text-white shadow-sm hover:bg-rose-700 focus:outline-none focus:ring-2 focus:ring-rose-500 focus:ring-offset-2">
    {{ text }}
  </button>
</template>

<script setup lang="ts">

interface Props {
  text: string
}

defineProps<Props>()

</script>

<style scoped>

</style>
