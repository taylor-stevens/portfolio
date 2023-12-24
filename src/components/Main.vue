<template>
  <v-container class="fill-height">
    <v-app-bar>
      <v-app-bar-nav-icon 
      color="deep-purple-accent-4" 
      icon="mdi-home-circle"
      @click="changePage(0)"/>
      <v-app-bar-title>{{ pageHeading }}</v-app-bar-title>
      Projects
      <v-btn icon="mdi-list-box" color="deep-purple-accent-4" @click="changePage(1)"/>
      Contact
      <v-btn icon="mdi-account-box" color="deep-purple-accent-4" @click="changePage(2)"/>
    </v-app-bar>
    <div v-if="page == 0">
      <Home @projects="changePage"/>
    </div>
    <div v-else-if="page == 1">
      <Projects/>
    </div>
    <div v-else-if="page == 2">
      <Contact/>
    </div>
  </v-container>
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
