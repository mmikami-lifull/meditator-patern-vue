<template>
  <v-card class="mx-auto" max-width="600">
    <v-card-title class="text-h3">
      Login
    </v-card-title>
    <v-card-text class="text-h6">
      <LoginTypes
        :currentLoginType="currentLoginType"
        @loginTypeClicked="loginTypeClicked"
      />
    </v-card-text>
    <v-card-actions>
    </v-card-actions>
  </v-card>
</template>

<script lang="ts">
import { Vue, Component } from 'vue-property-decorator'
import LoginTypes from "@/components/LoginTypes.vue"
import { LoginTypeEnum } from '@/lib/enum'

@Component({ components: { LoginTypes } })
export default class LoginFrame extends Vue {
  private currentLoginType = LoginTypeEnum["GUEST"]

  loginTypeClicked(type: LoginTypeEnum) {
    this.currentLoginType = type
  }
}
</script>
