<template>
  <div v-if="isLoading" class="h-full flex items-center justify-center text-gray-500 font-bold text-2xl">Loading...
  </div>
  <div v-else-if="isError" class="h-full flex items-center justify-center text-gray-500 font-bold text-2xl">An error has
    occurred: {{ error }}
  </div>
  <table class="w-full border-collapse bg-white text-left text-sm text-gray-500" v-else-if="data">
    <thead class="bg-gray-50">
    <tr>
      <th scope="col" class="px-6 py-4 font-medium text-gray-900">Subject</th>
      <th scope="col" class="px-6 py-4 font-medium text-gray-900">From</th>
      <th scope="col" class="px-6 py-4 font-medium text-gray-900">To</th>
    </tr>
    </thead>
    <tbody class="divide-y divide-gray-100 border-t border-gray-100">
    <tr class="hover:bg-gray-50 cursor-pointer" v-for="row in filterData" @click="$emit('setItem', row)"
        :class="{ visited: row._timestamp === itemSelected._timestamp }">
      <td class="flex gap-3 px-6 py-4 font-bold">
        {{ row.subject }}
      </td>
      <td class="px-6 py-4">
        {{ row.from }}
      </td>
      <td class="px-6 py-4">
        {{ row.to }}
      </td>
    </tr>
    </tbody>
  </table>
</template>
<script lang="ts">
import { defineComponent, PropType } from 'vue';
import { ItemSelectedType } from './entities/item';
import { useQuery } from '@tanstack/vue-query';

const fetcher = async (): Promise<ItemSelectedType[]> =>
    await fetch('https://fbd9-186-42-1-142.ngrok.io/feed/arora-h').then((response) =>
        response.json(),
    )

export default defineComponent({
  name: 'ItemsComponent',
  emits: ['setItem', 'setTotalEmails'],
  props: {
    itemSelected: {
      type: Object as PropType<ItemSelectedType>,
      required: true
    },
    textSearch: String
  },
  watch: {
    data(newItems: ItemSelectedType[]) {
      this.setTotalItems(newItems.length)
      this.filterData = newItems
    },
    textSearch(newTextSearch: string) {
      const filterData = this.data?.filter(item => {
        return item.content?.includes(newTextSearch)
      })
      this.filterData = filterData || []
      this.setTotalItems(this.filterData.length)
    },
  },
  methods: {
    setTotalItems(total: number) {
      this.$emit('setTotalEmails', total)
    }
  },
  setup() {
    const filterData: ItemSelectedType[] = [];
    const { isLoading, isError, isFetching, data, error, refetch } = useQuery({
      queryKey: ['feed'],
      queryFn: fetcher,
      refetchOnWindowFocus: false
    })

    return { isLoading, isError, isFetching, data, error, refetch, filterData }
  }
})
</script>

<style scoped>
.visited {
  @apply bg-rose-500 text-gray-100 !important;
}
</style>
