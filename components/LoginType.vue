<template>
  <v-radio-group :value="value">
    <v-radio
      :value="true"
      :label="label"
      @click="clicked"
    />
  </v-radio-group>
</template>

<script lang="ts">
import { Vue, Component, Prop } from 'vue-property-decorator'
import { LoginTypeEnum } from '~/lib/enum'

@Component
export default class LoginType extends Vue {
  @Prop()
  value!: boolean
  @Prop()
  name!: LoginTypeEnum

  get label() {
    switch(this.name) {
      case LoginTypeEnum["GUEST"]:
        return "Guest"
      case LoginTypeEnum["LOGIN"]:
        return "Login"
      default:
        throw new Error(`Unexpected name: ${this.name}`)
    }
  }

  clicked() {
    this.$emit("clicked", this.name)
  }
}
</script>
