<template>
  <v-app dark>
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant="miniVariant"
      :clipped="clipped"
      fixed
      app
    >
      <v-list>
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar app dense :clipped-left="$vuetify.breakpoint.lgAndUp">
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-divider class="mr-3" vertical></v-divider>
      <v-toolbar-title class="title mr-5">Shox Epress</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-divider class="ml-3" vertical></v-divider>
      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>
    </v-app-bar>
    <v-content>
      <nuxt />
    </v-content>
    <template>
      <v-bottom-navigation app grow>
        <v-btn @click.stop="sheet = !sheet">
          <span>Files</span>
          <v-icon>mdi-folder-open</v-icon>
        </v-btn>
        <v-divider vertical></v-divider>
        <v-btn @click.stop="sheet1 = !sheet1">
          <span>Upload</span>
          <v-icon>mdi-upload</v-icon>
        </v-btn>
        <v-divider vertical></v-divider>
        <v-btn @click.stop="sheet = !sheet">
          <span>Add</span>
          <v-icon>mdi-plus</v-icon>
        </v-btn>
        <v-divider vertical></v-divider>
        <v-btn @click.stop="sheet1 = !sheet1">
          <span>User</span>
          <v-icon>mdi-account</v-icon>
        </v-btn>
      </v-bottom-navigation>
    </template>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: 'mdi-apps',
          title: 'Welcome',
          to: '/'
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Inspire',
          to: '/inspire'
        }
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Vuetify.js'
    }
  }
}
</script>
