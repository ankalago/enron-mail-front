<template>
  <Disclosure as="nav" class="bg-gray-800" v-slot="{ open }">
    <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
      <div class="flex h-16 items-center justify-between">
        <div class="flex items-center">
          <div class="flex-shrink-0">
            <EmailIcon width="32" height="32" alt="Your Company"/>
          </div>
          <div class="hidden md:block">
            <div class="ml-10 flex items-baseline space-x-4">
              <h1 class="text-3xl font-bold tracking-tight text-gray-100">Mamuro Email</h1>
            </div>
          </div>
        </div>
        <div class="-mr-2 flex">
          <div class="col-span-3 sm:col-span-2">
            <div class="mt-1 flex rounded-md shadow-sm">
              <InputComponent/>
              <ButtonComponent text="Select"/>
            </div>
          </div>
        </div>
      </div>
    </div>
  </Disclosure>
</template>

<script>
import {Disclosure} from '@headlessui/vue'
import EmailIcon from './icons/EmailIcon.vue';
import ButtonComponent from './ButtonComponent.vue';
import InputComponent from './InputComponent.vue';

export default {
  name: "HeaderComponent",
  components: { InputComponent, Disclosure, EmailIcon, ButtonComponent }
}
</script>

