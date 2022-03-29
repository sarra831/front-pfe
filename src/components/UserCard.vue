<script setup>
import Level from '@/components/Level.vue'
import CardComponent from '@/components/CardComponent.vue'
</script>

<template>
  <card-component rounded="">
    <level type="justify-around lg:justify-center">
      <div class="space-y-3 text-center md:text-left lg:mx-12">
        <div class="flex justify-center md:block">
          <!--
          <check-radio-picker
            v-model="userSwitchVal"
            name="sample-switch"
            type="switch"
            :options="{ one: 'Notifications' }"
          /> -->
        </div>
        <h1 class="text-2xl">
          Bienvenue , <b>{{ userName }}</b>
        </h1>
        <p>Dernier Connexion <b>12 mins </b></p>
        <!--
        <div class="flex justify-center md:block">
          <pill
            text="Verified"
            type="info"
            :icon="mdiCheckDecagram"
          />
        </div> -->
      </div>
    </level>
  </card-component>
</template>
