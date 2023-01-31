<script setup lang="ts">
import { Disclosure } from '@headlessui/vue'
import EmailIcon from './components/icons/EmailIcon.vue';
import Button from './components/Button.vue';
</script>

<template>
  <div class="min-h-full">
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
                <input type="text" name="company-website" id="company-website"
                       class="block w-full flex-1 rounded-none rounded-l-md border-gray-300 focus:border-indigo-500 focus:ring-indigo-500 sm:text-sm"
                       placeholder="user ex: arora-h"/>
                <Button text="Select"/>
              </div>
            </div>
          </div>
        </div>
      </div>
    </Disclosure>

    <header class="bg-white shadow">
      <div class="mx-auto max-w-7xl py-6 px-4 sm:px-6 lg:px-8">
        <div class="grid grid-cols-2 gap-6">
          <div class="col-span-3">
            <div class="mt-1 flex rounded-md shadow-sm">
              <input type="text" name="company-website" id="company-website"
                     class="block w-full flex-1 rounded-none rounded-l-md border-gray-300 focus:border-indigo-500 focus:ring-indigo-500 sm:text-sm"
                     placeholder="search"/>
              <Button text="Search"/>
            </div>
          </div>
        </div>
      </div>
    </header>
    <main>
      <div class="mx-auto max-w-7xl py-2 md:py-6 sm:px-6 lg:px-8">

        <div class="md:grid md:grid-cols-7 md:gap-6">
          <div class="px-4 mt-5 md:col-span-3 md:mt-0">
            <!-- component -->
            <div class="overflow-hidden rounded-lg border border-gray-200 shadow-md">
              <table class="w-full border-collapse bg-white text-left text-sm text-gray-500">
                <thead class="bg-gray-50">
                <tr>
                  <th scope="col" class="px-6 py-4 font-medium text-gray-900">Subject</th>
                  <th scope="col" class="px-6 py-4 font-medium text-gray-900">From</th>
                  <th scope="col" class="px-6 py-4 font-medium text-gray-900">To</th>
                </tr>
                </thead>
                <tbody class="divide-y divide-gray-100 border-t border-gray-100">
                <tr class="hover:bg-gray-50">
                  <td class="flex gap-3 px-6 py-4 font-normal text-gray-900">
                    Subject
                  </td>
                  <td class="px-6 py-4">
                    <span
                        class="inline-flex items-center gap-1 rounded-full bg-green-50 px-2 py-1 text-xs font-semibold text-green-600"
                    >
                      <span class="h-1.5 w-1.5 rounded-full bg-green-600"></span>
                      Active
                    </span>
                  </td>
                  <td class="px-6 py-4">Product Designer</td>
                </tr>
                </tbody>
              </table>
            </div>
          </div>
          <div class="md:col-span-4">
            <div class="px-4 sm:px-0 mt-5 md:mt-0">
              <div class="overflow-hidden rounded-lg border border-gray-200 shadow-md p-5 h-max">
                content
              </div>
            </div>
          </div>
        </div>

      </div>
    </main>
  </div>
</template>
