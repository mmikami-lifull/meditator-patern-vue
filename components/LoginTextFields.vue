<template>
  <v-row>
    <v-col class="d-flex align-center" cols=3>
      <span>Username:</span> 
    </v-col>
    <v-col class="primary--text" cols=9>
      <LoginTextField
        :value="username"
        :disabled="disabled"
        @changed="usernameChanged"
      />
    </v-col>
    <v-col class="d-flex align-center" cols=3>
      <span>Password:</span> 
    </v-col>
    <v-col class="primary--text" cols=9>
      <LoginTextField
        :value="password"
        :disabled="disabled"
        :password="true"
        @changed="passwordChanged"
      />
    </v-col>
  </v-row>
</template>

<script lang="ts">
import { Vue, Component, Prop } from 'vue-property-decorator'
import LoginTextField from "@/components/LoginTextField.vue"

@Component({ components: { LoginTextField } })
export default class LoginTextFields extends Vue {
  @Prop()
  disabled!: boolean
  @Prop()
  username!: string
  @Prop()
  password!: string

  usernameChanged(v: string) {
    this.$emit("usernameChanged", v)
  }
  passwordChanged(v: string) {
    this.$emit("passwordChanged", v)
  }
}
</script>
