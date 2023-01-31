<template>
  <table class="w-full border-collapse bg-white text-left text-sm text-gray-500">
    <thead class="bg-gray-50">
    <tr>
      <th scope="col" class="px-6 py-4 font-medium text-gray-900">Subject</th>
      <th scope="col" class="px-6 py-4 font-medium text-gray-900">From</th>
      <th scope="col" class="px-6 py-4 font-medium text-gray-900">To</th>
    </tr>
    </thead>
    <tbody class="divide-y divide-gray-100 border-t border-gray-100">
    <tr class="hover:bg-gray-50 cursor-pointer" v-for="row in items" @click="$emit('setItem', row)">
      <td class="flex gap-3 px-6 py-4 font-normal text-gray-900">
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
import { defineComponent } from 'vue';
import { ItemSelectedType } from './entities/item';

const item1: ItemSelectedType = {
  from: "vic.gatto@owen2002.vanderbilt.edu",
  to: "harry.arora@enron.com",
  subject: "Thank You",
  origin: "arora-h",
  content: "Harry,\nThank you for taking time last week to meet with me and for arranging theother meetings as well.  I enjoyed our discussion and learning about thevarious opportunities within Enron.  I have been impressed with every groupat Enron.  I hope that we can keep in touch over the next few months.\nThank you again.\nSincerely,\n\nVic\n\nVic GattoOwen Graduate School of ManagementVanderbilt Universtiy(615) 292-7414vic.gatto@owen2002.vanderbilt.edu",
}
const item2: ItemSelectedType = {
  from: "maksym.yegorychev@owen2002.vanderbilt.edu",
  to: "harry.arora@enron.com",
  subject: "time to talk",
  origin: "arora-h",
  content: "Dear Harry,\nI would like to talk to you about the decision Enron made regarding summerinternship and how I could improve my chances next time. Could you advise meon the time to call you?\nBR,\nMaksym Yegorychev.",
}
const items: ItemSelectedType[] = [item1, item2, item1, item1, item2, item1, item1, item2, item1, item1, item2, item1, item1, item2, item1, item1, item2, item1, item1, item2, item1]
export default defineComponent({
  name: 'ItemsComponent',
  emits: ['setItem'],
  setup() {
    return {
      items,
    }
  }
})
</script>
