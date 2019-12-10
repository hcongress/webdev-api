<template>
  <v-app>
  <v-card class="overflow-hidden">
    <v-app-bar
      absolute
      dark
      color="#75c8ff"
      shrink-on-scroll
      prominent
      src="https://images.unsplash.com/photo-1501655433647-8f55b147bec0?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=2558&q=80"
      fade-img-on-scroll
      scroll-target="#scrolling-techniques-5"
      scroll-threshold="2000"
    >
      <template v-slot:img="{ props }">
        <v-img
          v-bind="props"
          gradient="to top right, rgba(227,250,255,.7), rgba(25,32,72,.7)"
        ></v-img>
      </template>

      <v-app-bar-nav-icon></v-app-bar-nav-icon>

      <v-toolbar-title class="headline">Pow-Pow Gnar-Gnar</v-toolbar-title>

    </v-app-bar>
    <v-sheet
      id="scrolling-techniques-5"
      class="overflow-y-auto"
      max-height="2000"
    >
      <v-container style="height: 1500px; margin-top: 100px;"> <HelloWorld/></v-container>
    </v-sheet>
  </v-card>

    <v-footer
    color= "#75c8ff"
    padless
  >
    <v-row
      justify="center"
      no-gutters
    >
      <v-btn
        v-for="link in links"
        :key="link"
        color="white"
        text
        rounded
        class="my-2"
      >
        {{ link }}
      </v-btn>
      <v-col
        class=" py-4 text-center white--text"
        cols="12"
      >
        {{ new Date().getFullYear() }} — <strong>Hunt-Hunt and Tom-Tom</strong>
      </v-col>
    </v-row>
  </v-footer>
  </v-app>
</template>

<script>
import HelloWorld from './components/HelloWorld'

export default {
  name: 'App',
  components: {
    HelloWorld
  },

  data: () => ({})
}
</script>
