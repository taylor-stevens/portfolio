<template>
  <v-sheet color="black" style="height: 100%;">
    <v-app-bar color="grey-darken-4">
      <template v-slot:prepend>
        <v-btn size="x-large" @click="page=0">
          <v-icon size="50">
            <v-img src="https://www.clker.com//cliparts/5/P/5/O/4/k/white-mountain-peak-ii-hi.png"/>
          </v-icon>
        </v-btn>
      </template>
      <v-tabs v-model="page" :color="tabColor">
        <v-tab value="0" :text="'Home'"></v-tab>
        <v-tab value="1" :text="'Projects'"></v-tab>
      </v-tabs>
    </v-app-bar>
    <Home v-if="page == 0" @projects="changePage"/>
    <Projects v-else-if="page == 1"/>
  </v-sheet>
</template>

<script>

  import Home from './Home.vue'
  import Projects from './Projects.vue'

  export default {
    // Properties returned from data() become reactive state
    // and will be exposed on `this`.
    data() {
      return {
        page: 0, //homepage
        pageHeading: 'Taylor Stevens', //homepage
        tabColor: 'white',
      }
    },

    // Methods are functions that mutate state and trigger updates.
    // They can be bound as event handlers in templates.
    methods: {
      changePage(page) {
        let initialPage = this.page
        this.page = page;
        this.pageHeading = this.page == 0 ? 'Taylor Stevens' : this.page == 1 ? 'Projects' : 'Unknown Page'
        this.$forceUpdate();
        console.log(`recieved page change from ${initialPage} to page ${page}`)
      },
    },
    components: {
      Home,
      Projects,
    }
  }
</script>
