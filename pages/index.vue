<template>
  <v-layout column justify-center align-center>
    <v-flex xs12 sm8 md6>
      <data-panel></data-panel>
    </v-flex>
  </v-layout>
</template>

<script>
import DataPanel from '~/components/data-panels.vue'

export default {
  components: {
    DataPanel
  }
}
</script>
