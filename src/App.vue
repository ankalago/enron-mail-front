<script lang="ts">
import { defineComponent, ref } from 'vue'

import ButtonComponent from './components/ButtonComponent.vue';
import HeaderComponent from './components/HeaderComponent.vue';
import ItemComponent from './components/ItemComponent.vue';
import { ItemSelectedType } from './entities/item';
import ItemsComponent from './ItemsComponent.vue';
import InputComponent from './components/InputComponent.vue';

export default defineComponent({
  name: 'App',
  components: { InputComponent, ItemsComponent, ButtonComponent, HeaderComponent, ItemComponent },
  setup() {
    const itemSelected = ref<ItemSelectedType>({})
    const totalEmails = ref<number>(0)
    const textSearch = ref<string>("")
    const textUser = ref<string>("")

    const setSearch = (text: string) =>
        textSearch.value = text

    const setUser = (text: string) =>
        textUser.value = text

    const setItem = (item: ItemSelectedType) =>
        itemSelected.value = item

    const setTotalEmails = (total: number) =>
        totalEmails.value = total

    return {
      setItem,
      itemSelected,
      setTotalEmails,
      totalEmails,
      setSearch,
      textSearch,
      textUser,
      setUser
    }
  }
})
</script>

<template>
  <div class="min-h-full">
    <HeaderComponent :totalEmails="totalEmails" @setUser="setUser"/>

    <header class="bg-white shadow">
      <div class="mx-auto max-w-7xl py-6 px-4 sm:px-6 lg:px-8">
        <div class="grid grid-cols-2 gap-6">
          <div class="col-span-3">
            <div class="mt-1 flex rounded-md shadow-sm">
              <InputComponent :placeHolder="`Filter by text in content`" @customChange="setSearch" :customClass="`rounded-md`"/>
            </div>
          </div>
        </div>
      </div>
    </header>

    <main class="mainHeight">
      <div class="mx-auto max-w-7xl py-2 md:py-6 sm:px-6 lg:px-8 md:grid md:grid-cols-7 md:gap-6 mainHeight">
        <div class="px-4 sm:px-0 mt-5 md:col-span-3 md:mt-0">
          <div class="overflow-auto rounded-lg border border-gray-200 shadow-md emailsHeight">
            <ItemsComponent @setItem="setItem" :itemSelected="itemSelected" @setTotalEmails="setTotalEmails"
                            :textSearch="textSearch" :textUser="textUser"/>
          </div>
        </div>
        <div class="md:col-span-4 px-4 sm:px-0 mt-5 md:mt-0">
          <div class="overflow-auto rounded-lg border border-gray-200 shadow-md p-5 emailsHeight">
            <ItemComponent v-if="itemSelected.origin" :itemSelected="itemSelected" :textSearch="textSearch"/>
            <span v-else class="h-full flex items-center justify-center text-gray-500 font-bold text-2xl">Select the email</span>
          </div>
        </div>
      </div>
    </main>
  </div>
</template>

<style scoped>
.mainHeight {
  height: calc(100vh - 158px);
}

.emailsHeight {
  height: calc(100vh - 200px);
}
</style>
