<script setup>
import { reactive } from 'vue'
import { useRouter } from 'vue-router'
import { mdiAccount, mdiAsterisk } from '@mdi/js'
import FullScreenSection from '@/components/FullScreenSection.vue'
import CardComponent from '@/components/CardComponent.vue'
import CheckRadioPicker from '@/components/CheckRadioPicker.vue'
import Field from '@/components/Field.vue'
import Control from '@/components/Control.vue'
import Divider from '@/components/Divider.vue'
import JbButton from '@/components/JbButton.vue'
import JbButtons from '@/components/JbButtons.vue'

const form = reactive({
  login: 'sarra',
  pass: 'highly-secure-password-fYjUw-',
  remember: ['remember']
})

const router = useRouter()

const submit = () => {
  router.push('/dashboard')
}
</script>

<template>
  <full-screen-section
    v-slot="{ cardClass, cardRounded }"
    bg="login"
  >
    <card-component
      :class="cardClass"
      :rounded="cardRounded"
      form
      @submit.prevent="submit"
    >
      <field
        label="Connexion"
        help="Entrez votre identifiant"
      >
        <control
          v-model="form.login"
          :icon="mdiAccount"
          name="login"
          autocomplete="username"
        />
      </field>

      <field
        label="Mot de passe"
        help="Entrez votre mot de passe"
      >
        <control
          v-model="form.pass"
          :icon="mdiAsterisk"
          type="password"
          name="Mot de passe"
          autocomplete="current-password"
        />
      </field>

      <check-radio-picker
        v-model="form.remember"
        name="remember"
        :options="{ remember: 'Remember' }"
      />

      <divider />

      <jb-buttons>
        <jb-button
          type="submit"
          color="info"
          label="Connexion"
        />
        <jb-button
          to="/dashboard"
          color="info"
          outline
          label="Retour"
        />
      </jb-buttons>
    </card-component>
  </full-screen-section>
</template>
