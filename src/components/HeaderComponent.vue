<template>
  <Disclosure as="nav" class="bg-gray-800" v-slot="{ open }">
    <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
      <div class="flex h-16 items-center justify-between">
        <div class="flex items-center">
          <div class="flex-shrink-0">
            <EmailIcon width="32" height="32" alt="Your Company"/>
          </div>
          <div class="ml-2 sm:ml-10 flex items-baseline sm:space-x-4">
            <h1 class="hidden sm:block text-2xl md:text-3xl font-bold tracking-tight text-gray-100">Mamuro Email</h1> <span class="text-2xl md:text-3xl font-bold tracking-tight text-gray-100">({{ totalEmails }})</span>
          </div>
        </div>
        <div class="-mr-2 flex">
          <div class="col-span-3 sm:col-span-2">
            <div class="mt-1 flex rounded-md shadow-sm">
              <InputComponent :placeHolder="`user (ex: arora-h)`" :customClass="`rounded-l-md`"
                              @customChange="setTextUser"/>
              <ButtonComponent text="Select" :onClick="onClick"/>
            </div>
          </div>
        </div>
      </div>
    </div>
  </Disclosure>
</template>

<script lang="ts">
import { Disclosure } from '@headlessui/vue'
import EmailIcon from './icons/EmailIcon.vue';
import ButtonComponent from './ButtonComponent.vue';
import InputComponent from './InputComponent.vue';
import { defineComponent } from 'vue';

export default defineComponent({
  name: "HeaderComponent",
  props: {
    totalEmails: Number,
    textUser: String
  },
  components: { InputComponent, Disclosure, EmailIcon, ButtonComponent },
  emits: ['setUser'],
  methods: {
    setTextUser(text: string) {
      this.textUser = text
    },
    onClick() {
      this.$emit('setUser', this.textUser)
    }
  },
  setup() {
    const textUser: string = ""
    return {
      textUser
    }
  }
})
</script>

