<template>
  <v-row class="justify-center">
    <v-col cols=3>
      <LoginActionButton
        title="ok"
        :dark="true"
      />
    </v-col>
    <v-col cols=3>
      <LoginActionButton
        title="cancel"
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
  disabled!: boolean

  clicked() {
    this.$emit("clicked")
  }
}
</script>
