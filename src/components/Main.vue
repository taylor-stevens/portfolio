<template>
  <v-app-bar color="grey-darken-3">
      <v-app-bar-title>{{ pageHeading }}</v-app-bar-title>
      <v-tabs
                  show-arrows
                  v-model="page"
                  height="60"
                >
                  <v-tab value="0" :text="'Home'"></v-tab>
                  <v-tab value="1" :text="'Projects'"></v-tab>
                  <v-tab value="2" :text="'Contact'"></v-tab>
              </v-tabs>
    </v-app-bar>
    <Home v-if="page == 0" @projects="changePage"/>
    <Projects v-else-if="page == 1"/>
    <Contact v-else-if="page == 2"/>
</template>

<script>

  import Home from './Home.vue'
  import Projects from './Projects.vue'
  import Contact from './Contact.vue'

  export default {
    // Properties returned from data() become reactive state
    // and will be exposed on `this`.
    data() {
      return {
        page: 0, //homepage
        pageHeading: 'Taylor Stevens' //homepage
      }
    },

    // Methods are functions that mutate state and trigger updates.
    // They can be bound as event handlers in templates.
    methods: {
      changePage(page) {
        let initialPage = this.page
        this.page = page;
        this.pageHeading = this.page == 0 ? 'Taylor Stevens' : this.page == 1 ? 'Projects' : this.page == 2 ? 'Contact Me' : 'Unknown Page'
        this.$forceUpdate();
        console.log(`recieved page change from ${initialPage} to page ${page}`)
      },
    },

    components: {
      Home,
      Projects,
      Contact
    }
  }
</script>
