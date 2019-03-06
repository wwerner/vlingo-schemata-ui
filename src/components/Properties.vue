<template>

<v-card min-height="30rem">
  <v-card-text>
  <v-tabs>
    <v-tab>Specification</v-tab>
    <v-tab>Status</v-tab>
    <v-tab>Description</v-tab>

    <v-tab-item>Specification for {{ schema }}</v-tab-item>
    <v-tab-item>Status for {{ schema }}</v-tab-item>
    <v-tab-item>Description for {{ schema }}</v-tab-item>
  </v-tabs>
  </v-card-text>

</v-card>


</template>

<script>
export default {
  props: ['schema'],
  data: () => ({})
}
</script>

<style>
.v-card {
  overflow-y: auto
}
</style>
