<script setup>
import { useStore } from 'vuex'
import { computed } from 'vue'

const store = useStore()

const lightBgStyle = computed(() => store.state.lightBgStyle)
</script>

<template>
  <div>
    <img
      :src="avatar"
      :alt="name"
      class="rounded-full block h-auto w-full max-w-full dark:bg-gray-800"
      :class="lightBgStyle"
    >
  </div>
</template>
