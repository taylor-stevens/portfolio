<template>
    <v-container class="fill-height transparent">
      <v-row>
        <v-col style="padding: 3%;">
          <v-img
            cols="auto"
            lg="3"
            sm="6"
            class="bg-white rounded-xl"
            :aspect-ratio="1"
            src="../assets/me.jpeg"
            cover
          ></v-img>
        </v-col>
        <v-col sm="6" lg="5" cols="auto" style="place-self:center; min-width: 50%;">
          <div>
            <div class="text-h5">About</div>
            <br>
            My name is Taylor Stevens and I am a Software Engineer with a degree in Computer Science concentrated in Artificial 
            Intelligence from Northeastern University. I recently graduated magna cum laude in December 2023 and I am excited to
            begin working my first full time job post-grad. I have a diverse background with full-stack development having worked
            with a broad range of tools and environments from React and Linux to Git and Pyspark. Driven by a passion for public 
            service and mutual aid, I have worked on many projects that given me experience in complex problem-solving, leadership, 
            and collaboration.
            <br><br>
            One project that I am particularly proud of is the FosteredFood project, a mutual aid initiative that focuses on reducing food 
            waste and increasing food access for low-income and food-insecure individuals. As the project lead, I have been able to expand 
            and develop my skills in project management and community outreach as well as my technical skills with Typescript, React, Google 
            API's, and more. 
            <br><br>
            My personal interests include playing rugby as a wing, going bouldering indoors and outdoors, and hiking and camping in the White 
            Mountains in New Hampshire.
            <br><br>
            To explore some of my projects, navigate using the tabs in the upper right corner.
          </div>
        </v-col>
      </v-row>
    </v-container>
</template>

<script>
  export default {
    props: ['page', 'changePage'],
    methods: {
      projectsClicked() {
        this.$emit('projects', 1)
      }
    },
    data() {
      return {
      }
    }
  }
</script>
