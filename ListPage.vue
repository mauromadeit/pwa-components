<template>
  <v-container>
    <v-layout>
      <v-flex xs12 sm8 offset-sm2 md6 offset-md3>
        <v-card>
          <list header="{{ title atom }}s" v-bind="{items, edit}" />
        </v-card>
      </v-flex>
      <v-btn fixed fab bottom right
        class="red" dark
        @click="add{{ title atom }}().then(id => $router.push(`/{{atom}}/${id}/edit`))"
        >
        <v-icon>add</v-icon>
      </v-btn>
    </v-layout>
  </v-container>
</template>

<script>
  import List from './List'
  import {mapState, mapActions} from 'vuex'

  export default {
    components: {
      List
    },
    computed: {
      ...mapState(['{{atoms}}']),
      items() {
        return this.{{atoms}}.map(e => ({...e, label: e.description}))
      },
    },
    methods: {
      ...mapActions(['add{{ title atom }}']),
      edit(item) {
        this.$router.push(`/{{atom}}/${item.id}/edit`)
      },
    },
  }
</script>
