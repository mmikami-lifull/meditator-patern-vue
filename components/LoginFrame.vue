<template>
  <v-card class="mx-auto" max-width="600">
    <v-card-title class="text-h3 primary">
      <span class="mx-auto white--text">Login</span>
    </v-card-title>
    <v-card-text class="text-h6 pl-6">
      <LoginTypes
        :currentLoginType="currentLoginType"
        @clicked="setLoginType"
      />
      <LoginTextFields
        :disabled="!canEditFields"
        :username="username"
        :password="password"
        @usernameChanged="setUsername"
        @passwordChanged="setPassword"
      />
    </v-card-text>
    <v-card-actions>
      <LoginActionButtons
        :okDisabled="!canClickOk"
        @okClicked="okClicked"
        @cancelClicked="cancelClicked"
      />
    </v-card-actions>
  </v-card>
</template>

<script lang="ts">
import { Vue, Component } from 'vue-property-decorator'
import LoginTypes from "@/components/LoginTypes.vue"
import LoginTextFields from "@/components/LoginTextFields.vue"
import LoginActionButtons from "@/components/LoginActionButtons.vue"
import { LoginTypeEnum } from '@/lib/enum'

const auth = {
  username: "username",
  password: "password",
}

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
  private username = ""
  private password = ""

  get isTypeLogin() {
    return this.currentLoginType === LoginTypeEnum["LOGIN"]
  }
  get canEditFields() {
    return this.isTypeLogin
  }
  get canClickOk() {
    return (
      this.isTypeLogin
      && this.username
      && this.password
    )
  }

  init() {
    this.currentLoginType = LoginTypeEnum["GUEST"]
    this.username = ""
    this.password = ""
  }
  setLoginType(type: LoginTypeEnum) {
    this.currentLoginType = type
  }
  setUsername(username: string) {
    this.username = username
  }
  setPassword(password: string) {
    this.password = password
  }
  okClicked() {
    const msg = 
      this.validateAuth()
      ? "Login success"
      : "Invalid auth"
    window.alert(msg)
  }
  cancelClicked() {
    this.init()
  }
  validateAuth() {
    return (
      this.username === auth.username
      && this.password === auth.password
    )
  }
}
</script>
