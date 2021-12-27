<template>
  <v-btn
    :disabled="disabled"
    :dark="dark"
    :color="color"
    depressed
    min-width="120"
    @click="clicked"
  >
    {{ title }}
  </v-btn>
</template>

<script lang="ts">
import { Vue, Component, Prop } from 'vue-property-decorator'

@Component
export default class LoginActionButton extends Vue {
  @Prop()
  title!: string
  @Prop({ default: false })
  disabled!: boolean
  @Prop({ default: false })
  dark!: boolean
  @Prop({ default: undefined })
  color!: string

  clicked() {
    this.$emit("clicked")
  }
}
</script>
