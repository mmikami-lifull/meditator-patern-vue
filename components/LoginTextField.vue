<template>
  <v-text-field
    v-model="value"
    :disabled="disabled"
    :type="type"
  />
</template>

<script lang="ts">
import { Vue, Component, Prop, Watch } from 'vue-property-decorator'

@Component
export default class LoginTextField extends Vue {
  private value = ""

  @Prop()
  disabled!: boolean

  @Prop({ default: false })
  password!: boolean

  @Watch("value")
  onValueChanged(v: string) {
    this.$emit("changed", v)
  }

  get type() {
    if(this.password) return "password"
    return "text"
  }
}
</script>
