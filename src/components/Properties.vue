<template>

<v-card min-height="30rem">
  <v-card-text>
  <v-tabs>
    <v-tab>Specification</v-tab>
    <v-tab>Status</v-tab>
    <v-tab>Description</v-tab>

    <v-tab-item>Specification for {{ schema }} <span v-if="version">v{{ version }}</span></v-tab-item>
    <v-tab-item>Status for {{ schema }}<span v-if="version">v{{ version }}</span></v-tab-item>
    <v-tab-item>
      Description for {{ schema }} <span v-if="version">v{{ version }}</span>
      <div v-html="compiledDescription()"></div>
    </v-tab-item>
  </v-tabs>
  </v-card-text>

</v-card>


</template>

<script>
import marked from 'marked'

export default {
  props: ['schema', 'version'],
  data: () => ({
    status: [],
    specification: '',
    description: ''
  }),
  watch: {
    schema: function () {
      this.fetchData()
    },
    version: function () {
      this.fetchData()
    },
  },
  methods: {
    fetchData() {
      this.status = []
      this.specification = ''
      this.description = ''
      // TODO: query an actual backend, this is just mock data
      if (this.schema === "com.google.search.adwords.events.AdWordsAudienceChosen" && this.version === "1.0.1") {
        this.status = ['Draft', 'Published']
        this.specification = 'Foo'
        this.description = '# Description\nAlso\n* supports\n* **Mark**_down_'
      } else if (this.schema === "com.google.search.adwords.events.AdWordsAudienceChosen" && this.version === "1.0.0") {
        this.status = ['Draft']
        this.specification = 'Bar'
        this.description = '**B**_a_z'
      }  else if (this.schema === "com.google.search.adwords.events.AdWordsAccountCreated" && this.version === "1.0.0") {
        this.status = ['Published']
        this.specification = 'Qux'
        this.description = '_Quux_'
      }  else if (this.schema === "com.google.search.adwords.events.AdWordsLocationCreated" && this.version === "1.0.0") {
        this.status = ['Published','Deprectated']
        this.specification = 'corge'
        this.description = '# grault'
      }
    },
    compiledDescription: function () {
      return marked(this.description, { sanitize: true })
    }
  }
}
</script>

<style>
.v-card {
  overflow-y: auto
}
</style>
