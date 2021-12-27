<template>
  <v-card class="mx-auto" max-width="600">
    <v-card-title class="text-h3">
      <span class="mx-auto">LOGIN</span>
    </v-card-title>
    <v-card-text class="text-h6 pl-6">
      <LoginTypes
        :currentLoginType="currentLoginType"
        @clicked="loginTypeClicked"
      />
      <LoginTextFields
        @usernameChanged="usernameChanged"
        @passwordChanged="passwordChanged"
      />
    </v-card-text>
    <v-card-actions>
      <LoginActionButtons />
    </v-card-actions>
  </v-card>
</template>

<script lang="ts">
import { Vue, Component } from 'vue-property-decorator'
import LoginTypes from "@/components/LoginTypes.vue"
import LoginTextFields from "@/components/LoginTextFields.vue"
import LoginActionButtons from "@/components/LoginActionButtons.vue"
import { LoginTypeEnum } from '@/lib/enum'

@Component(
  { 
    components: { 
      LoginTypes ,
      LoginTextFields,
      LoginActionButtons,
    }
  }
)
export default class LoginFrame extends Vue {
  private currentLoginType = LoginTypeEnum["GUEST"]

  loginTypeClicked(type: LoginTypeEnum) {
    this.currentLoginType = type
  }
  usernameChanged(username: string) {
    console.log("username: ", username)
  }
  passwordChanged(password: string) {
    console.log("password: ", password)
  }
}
</script>
