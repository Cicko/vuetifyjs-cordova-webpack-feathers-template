<template>
  <v-app>
    <v-navigation-drawer
      persistent
      v-model="drawer"
      enable-resize-watcher
      fixed
      app
    >
      <v-list>
        <v-list-tile
          value="true"
          v-for="(item, i) in items"
          :key="i"
        >
          <v-list-tile-action>
            <v-icon v-html="item.icon"></v-icon>
          </v-list-tile-action>
          <v-list-tile-content @click="$router.push(item.path)">
            <v-list-tile-title v-text="item.title"></v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
    <v-toolbar
      app
    >
      <v-toolbar-side-icon @click.stop="drawer = !drawer"></v-toolbar-side-icon>
      <v-toolbar-title v-text="title"></v-toolbar-title>
    </v-toolbar>
    <v-content>
      <router-view/>
    </v-content>
    <v-footer :fixed="fixed" app>
      <span>&copy; Rudolf Cicko 2018</span>
    </v-footer>
  </v-app>
</template>

<style>
  .toolbar__content {
    height: 44px !important;
  }
</style>

<script>
export default {
  data () {
    return {
      drawer: false,
      fixed: false,
      items: [{
        icon: 'list',
        title: 'List',
        path: '/list'
      }, {
        icon: 'content_paste',
        title: 'Form',
        path: '/form'
      }],

      title: 'Budgi'
    }
  },
  name: 'App'
}
</script>
