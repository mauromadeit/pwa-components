<template>
  <v-container>
    <v-layout>
      <v-flex xs12 sm8 offset-sm2 md6 offset-md3>
        <v-card>
          <v-card-text>
            <form>
              <v-text-field v-model="{{atom}}.description"
                class="mt-2" label="Description" />
            </form>
          </v-card-text>
          <v-card-actions>
            <v-spacer />
            <v-btn class="blue white--text" @click="save">
              Save
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
  export default {
    props: ['id'],
    computed: {
      {{atom}}() { return this.$store.getters.{{atom}}ById(this.id) },
      payload() {
        if (this.{{atom}}) {  // TODO how else can this be fixed?
          return {
            ...this.{{atom}},
            id: this.id,
          }
        }
      },
    },
    methods: {
      save() {
        this.$store.dispatch('update{{ title atom }}', this.payload)
        .then(() => this.$router.push(`/`))
      },
    },
  }
</script>
