<template>
  <v-app>
    <v-app-bar id="header" color="primary lighten-1" dark app>
      <v-app-bar-nav-icon></v-app-bar-nav-icon>

      <v-toolbar-title>WE CARE</v-toolbar-title>

      <v-btn
        v-for="(link,idx) in linksHeader"
        :key="idx"
        color="white"
        text
        rounded
        class="my-2"
      >
        <nuxt-link :to="{ path: link.path }">{{ link.name }}</nuxt-link>
      </v-btn>

      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>mdi-heart</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>

      <v-menu left bottom>
        <template v-slot:activator="{ on, attrs }">
          <v-btn icon v-bind="attrs" v-on="on">
            <v-icon>mdi-dots-vertical</v-icon>
          </v-btn>
        </template>

        <v-list>
          <v-list-item v-for="n in 5" :key="n" @click="() => {}">
            <v-list-item-title>Option {{ n }}</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>
    </v-app-bar>
    <v-main>
      <v-container>
        <nuxt />
      </v-container>
    </v-main>
    <v-footer color="primary lighten-1" padless>
      <v-row justify="center" no-gutters>
        <v-btn
          v-for="(link,idx) in linksFooter"
          :key="idx"
          color="white"
          text
          rounded
          class="my-2"
        >
          {{ link }}
        </v-btn>
        <v-col class="primary lighten-2 py-4 text-center white--text" cols="12">
          {{ new Date().getFullYear() }} — <strong>WE CARE</strong>
        </v-col>
      </v-row>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data: () => ({
    linksHeader: [
      {
        name: 'home',
        path: '/',
      },
      {
        name: 'news',
        path: '/news',
      },
      {
        name: 'contents',
        path: '/contents',
      },
      {
        name: 'professionals',
        path: '/professionals',
      },
    ],
    linksFooter: ['home', 'about us', 'team', 'services', 'contact Us'],
  }),
}
</script>

<style lang="scss">
#app {
  background-image: url('~/static/background01.png');
  background-repeat: no-repeat;
  background-size: cover;
}

#header {
  a:link,
  a:visited,
  a:active {
    text-decoration: none;
    color: inherit;
  }
}
</style>
