<template>

<v-card min-height="30rem">
  Versions for {{ schema }}
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
