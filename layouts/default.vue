<template>
  <v-app light>

    <!--- --->
    <v-navigation-drawer
      v-model="drawer"
      
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
<!--  -->


    <!-- drawer items -->
    <v-app-bar :clipped-left="clipped" fixed app>
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-toolbar-title v-text="title" />
    </v-app-bar>
    <!-- drawer items -->



  <!-- main -->
    <v-main>
      <v-container>
        <nuxt />
      </v-container>
    </v-main>
  <!--main -->


    <footer-component></footer-component>
  </v-app>
</template>

<script>
import FooterComponent from '~/components/FooterComponent.vue'

export default {
  components: {
    FooterComponent,
  },
   methods: {
    toggleDrawer() {
      this.$refs.drawer.toggleDrawer()
    },
  },
  data() {
    return {
      title:'Titel',
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: 'mdi-apps',
          title: 'Welcome',
          to: '/',
        },
        {
          icon: 'mdi-apps',
          title: 'test',
          to: '/test',
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Blog',
          to: '/blog',
        },
      ],


    }
  },
}
</script>
