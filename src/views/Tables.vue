<script setup>
import { ref } from 'vue'
import MainSection from '@/components/MainSection.vue'
import Notification from '@/components/Notification.vue'
import ClientsTable from '@/components/ClientsTable.vue'
import CardComponent from '@/components/CardComponent.vue'
import TitleBar from '@/components/TitleBar.vue'
import HeroBar from '@/components/HeroBar.vue'
import BottomOtherPagesSection from '@/components/BottomOtherPagesSection.vue'
import TitleSubBar from '@/components/TitleSubBar.vue'

const titleStack = ref(['Admin', 'Tables'])
</script>

<template>
  <title-bar :title-stack="titleStack" />
  <hero-bar>Tables</hero-bar>
  <main-section>
      <card-component
      class="mb-6"
      title="Sociétés "
      :icon="mdiAccountMultiple"
      has-table
    >
      <clients-table checkable />
    </card-component>

    <title-sub-bar
      :icon="mdiTableBorder"
      title="Variante enveloppée "
    />
    <card-component
      class="mb-6"
      has-table
    >
      <clients-table checkable />
    </card-component>

    <title-sub-bar
      :icon="mdiTableOff"
      title="Variation vide"
    />

    <notification
      color="danger"
      :icon="mdiTableOff"
    >
      <b>Tableau vide.</b> Quand il n'y a rien à montrer.
    </notification>

    <card-component empty />
  </main-section>

  <bottom-other-pages-section />
</template>
