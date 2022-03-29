<script setup>
import { ref, reactive } from 'vue'
import { useStore } from 'vuex'
import { mdiAccount, mdiAccountCircle, mdiLock, mdiMail, mdiAsterisk, mdiFormTextboxPassword } from '@mdi/js'
import MainSection from '@/components/MainSection.vue'
import CardComponent from '@/components/CardComponent.vue'
import TitleBar from '@/components/TitleBar.vue'
import Divider from '@/components/Divider.vue'
import Field from '@/components/Field.vue'
import Control from '@/components/Control.vue'
import JbButton from '@/components/JbButton.vue'
import BottomOtherPagesSection from '@/components/BottomOtherPagesSection.vue'
import JbButtons from '@/components/JbButtons.vue'
import UserCard from '@/components/UserCard.vue'

const store = useStore()

const titleStack = ref(['Admin', 'Profile'])

const profileForm = reactive({
  name: store.state.userName,
  email: store.state.userEmail
})

const passwordForm = reactive({
  password_current: '',
  password: '',
  password_confirmation: ''
})

const submitProfile = () => {
  store.commit('user', profileForm)
}

const submitPass = () => {
  //
}
</script>

<template>
  <title-bar :title-stack="titleStack" />

  <user-card />

  <main-section>
    <div class="grid grid-cols-1 lg:grid-cols-2 gap-6">
      <card-component
        title="Editer Profil"
        :icon="mdiAccountCircle"
        form
        @submit.prevent="submitProfile"
      >
      <!--
        <field
          label="Avatar"
          help="Max 500kb"
        >
          <file-picker />
        </field> -->

        <field
          label="Nom"
          help="Obligatoire. Votre Nom"
        >
          <control
            v-model="profileForm.name"
            :icon="mdiAccount"
            name="username"
            required
            autocomplete="username"
          />
        </field>
        <field
          label="E-mail"
          help="Obligatoire. Votre e-mail"
        >
          <control
            v-model="profileForm.email"
            :icon="mdiMail"
            type="email"
            name="email"
            required
            autocomplete="email"
          />
        </field>

        <divider />

        <jb-buttons>
          <jb-button
            color="info"
            type="submit"
            label="Confirmer"
          />
          <jb-button
            color="info"
            label="Options"
            outline
          />
        </jb-buttons>
      </card-component>

      <card-component
        title="Changer Mot de passe "
        :icon="mdiLock"
        form
        @submit.prevent="submitPass"
      >
        <field
          label="Mot de passe actuel"
          help="Obligatoire. Votre Mot de passe actuel"
        >
          <control
            v-model="passwordForm.password_current"
            :icon="mdiAsterisk"
            name="password_current"
            type="password"
            required
            autocomplete="current-password"
          />
        </field>

        <divider />

        <field
          label="Nouveau Mot de passe"
          help="Confirmer votre Mot de passe  "
        >
          <control
            v-model="passwordForm.password"
            :icon="mdiFormTextboxPassword"
            name="Mot de passe"
            type="password"
            required
            autocomplete="new-password"
          />
        </field>

        <field
          label="Confirmer Mot de passe "
          help="Required. New password one more time"
        >
          <control
            v-model="passwordForm.password_confirmation"
            :icon="mdiFormTextboxPassword"
            name="password_confirmation"
            type="password"
            required
            autocomplete="new-password"
          />
        </field>

        <divider />

        <jb-buttons>
          <jb-button
            type="submit"
            color="info"
            label="Confirmer"
          />
          <jb-button
            color="info"
            label="Options"
            outline
          />
        </jb-buttons>
      </card-component>
    </div>
  </main-section>

  <bottom-other-pages-section />
</template>
