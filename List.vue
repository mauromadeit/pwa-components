<template>
  <v-list>
    <v-subheader>
      \{{ header }}
    </v-subheader>
    <template v-for="(item,i) in items">
      <v-divider class="mb-1"></v-divider>
      <v-list-tile :key="i" @click="$router.push('/item/'+item.id)">
        <v-list-tile-content>
          <v-list-tile-title>
            \{{ item.label }}
          </v-list-tile-title>
        </v-list-tile-content>
        <v-list-tile-action>
          <v-btn icon @click="edit(item)">
            <v-icon class="grey--text text--lighten-1">edit</v-icon>
          </v-btn>
        </v-list-tile-action>
      </v-list-tile>
    </template>
  </v-list>
</template>

<script>
  export default {
    props: ['items', 'header', 'edit'],
  }
</script>
