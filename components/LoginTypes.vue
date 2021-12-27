<template>
  <v-row>
    <v-col class="d-flex align-center" cols=12 md=3>
      <span>Login type:</span> 
    </v-col>
    <v-col class="primary--text" cols=12 md=3>
      <LoginType
        :value="guestValue" 
        :name="guestName"
        @clicked="clicked"
      />
    </v-col>
    <v-col class="primary--text" cols=12 md=3>
      <LoginType
        :value="loginValue"
        :name="loginName"
        @clicked="clicked"
      />
    </v-col>
  </v-row>
</template>

<script lang="ts">
import { Vue, Component, Prop } from 'vue-property-decorator'
import LoginType from "@/components/LoginType.vue"
import { LoginTypeEnum } from "@/lib/enum"

@Component({ components: { LoginType } })
export default class LoginTypes extends Vue {
  @Prop()
  currentLoginType!: LoginTypeEnum

  get guestName() {
    return LoginTypeEnum["GUEST"]
  }
  get loginName() {
    return LoginTypeEnum["LOGIN"]
  }
  get guestValue() {
    return this.currentLoginType === this.guestName
  }
  get loginValue() {
    return this.currentLoginType === this.loginName
  }

  clicked(type: LoginTypeEnum) {
    this.$emit("clicked", type)
  }
}
</script>
