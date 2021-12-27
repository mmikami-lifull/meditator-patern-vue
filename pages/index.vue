<template>
  <v-container class="fill-height">
    <v-row align="center" justify="center">
      <v-col cols="12" md="6">
        <LoginFrame />
      </v-col>
    </v-row>
  </v-container>
</template>

<script lang="ts">
import { Vue, Component } from 'vue-property-decorator'
import LoginFrame from "@/components/LoginFrame.vue"

@Component({ components: { LoginFrame } })
export default class IndexPage extends Vue {}
</script>
