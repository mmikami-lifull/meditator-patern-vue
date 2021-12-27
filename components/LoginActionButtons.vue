<template>
  <v-row class="justify-center">
    <v-col cols=3>
      <LoginActionButton
        color="primary"
        title="ok"
        :disabled="okDisabled"
        :dark="dark"
        @clicked="okClicked"
      />
    </v-col>
    <v-col cols=3>
      <LoginActionButton
        title="cancel"
        @clicked="cancelClicked"
      />
    </v-col>
  </v-row>
</template>

<script lang="ts">
import { Vue, Component, Prop } from 'vue-property-decorator'
import LoginActionButton from "@/components/LoginActionButton.vue"

@Component({ components: { LoginActionButton } })
export default class LoginActionButtons extends Vue {
  @Prop()
  title!: string

  @Prop()
  okDisabled!: boolean

  get dark() {
    return !this.okDisabled
  }

  okClicked() {
    this.$emit("okClicked")
  }
  cancelClicked() {
    this.$emit("cancelClicked")
  }
}
</script>
