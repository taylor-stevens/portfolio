<template>
    <v-container class="fill-height transparent" style="max-height: 90vh;">
      <v-row style="max-height:inherit">
        <v-col style="padding: 3%;" cols="12" sm="6" align-self="center">
          <div class="text-h1">{{ 'Taylor Stevens' }}</div>
        </v-col>
        <v-col cols="12" sm="6" style="max-height: inherit; overflow: scroll; padding-top: 5%; padding-bottom: 20%;">
          <div>
            <div class="text-h7" style="overflow-y: auto">
              <br>
              Welcome to my software engineering portfolio! Here, you'll find examples of 
            projects I worked on while studying. Whether you're here to browse through my projects, learn more 
            about my experience, or get in touch for potential collaboration, I hope you 
            find what you're looking for!
            <br/><br/>
            Some of the projects that I have had the pleasure of working on, which can 
            be found in more detail on my 
            <v-btn size="small" @click="projectsClicked(1)" color="transparent">Projects</v-btn>
            page, include the following: The FosteredFood Web Application, A Multinomial 
            Regression Final Project, and A Covey Town Application Extension. On each 
            page, a quick view of the tech stacks are by logo view on the side of each
            page's main image. 
            <br/><br/>
            I am a passionate software engineer with over 1 year of experience in building 
            web applications, writing extensive testing coverage, and using data analysis
            tools, and a four year degree in Computer Science and Artificial Intelligence
            from Northeastern University. My journey in software development began in high 
            school my sophomore year, where I discovered my love for coding and 
            problem-solving, but did not stop there!
            <br/><br/>
            I thrive in collaborative environments where creativity and innovation are 
            encouraged, and I enjoy tackling complex technical challenges. My skill set 
            includes proficiency in a wide range of technologies, from backend development 
            using Python and Javascript to frontend frameworks like React, Vue, and SwiftUI.
            <br/><br/>
            If you are interested in discussing a project or exploring opportunities to 
            work together, feel free to reach out via email at taylorstevens14562@gmail.com. 
            I'm always open to new challenges and eager to contribute to impactful projects.
            <br/><br/>
            Thank you for visiting my portfolio, and I look forward to connecting with you!
            </div>
          </div>
        </v-col>
      </v-row>
    </v-container>
</template>

<script>
  export default {
    props: ['page', 'changePage'],
    methods: {
      projectsClicked(num) {
        this.$emit('projects', num)
      }
    },
    data() {
      return {
      }
    }
  }
</script>
