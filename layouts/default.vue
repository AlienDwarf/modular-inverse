<template>
  <v-app dark>
    <v-app-bar
      :clipped-left="clipped"
      fixed
      app
    >
      <v-toolbar-title v-text="title" />
    </v-app-bar>
    <v-main>
      <v-container>
        <nuxt />
      </v-container>
    </v-main>
    <v-footer
      :absolute="!fixed"
      app
    >
      <span>{{ new Date().toLocaleDateString() }}</span>
      <v-spacer />
      <span>{{ time }}</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data () {
    return {
      time: new Date().toLocaleTimeString(),
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
      title: 'Modular Inverse Finder'
    }
  },
  mounted() {
    setInterval(() => {
      return this.time = new Date().toLocaleTimeString();
    }, 1000);
  }
}
</script>
