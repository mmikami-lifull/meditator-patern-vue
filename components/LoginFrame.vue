<template>
  <v-card class="mx-auto" max-width="600">
    <v-card-title class="text-h3 primary">
      <span class="mx-auto white--text">Login</span>
    </v-card-title>
    <v-card-text class="text-h6 pl-6">
      <LoginTypes
        :currentLoginType="currentLoginType"
        @clicked="loginTypeClicked"
      />
      <LoginTextFields
        :disabled="textFieldsDisabled"
        :username="username"
        :password="password"
        @usernameChanged="usernameChanged"
        @passwordChanged="passwordChanged"
      />
    </v-card-text>
    <v-card-actions>
      <LoginActionButtons
        :okDisabled="okBtnDisabled"
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

  get isTypeGuest() {
    return this.currentLoginType === LoginTypeEnum["GUEST"]
  }
  get textFieldsDisabled() {
    return this.isTypeGuest
  }
  get okBtnEnabled() {
    return (
      !this.isTypeGuest
      && this.username
      && this.password
    )
  }
  get okBtnDisabled() {
    return !this.okBtnEnabled
  }

  init() {
    this.currentLoginType = LoginTypeEnum["GUEST"]
    this.username = ""
    this.password = ""
  }
  loginTypeClicked(type: LoginTypeEnum) {
    this.currentLoginType = type
  }
  usernameChanged(username: string) {
    this.username = username
  }
  passwordChanged(password: string) {
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
