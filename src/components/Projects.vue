<template>
    <v-container justify="center" justify-self="center">
        <v-row no-gutters justify="center">
            <v-tabs v-for="project in projectData" v-model="tab" fixed-tabs center-active show-arrows>
                <v-tab :value="project.name" :text="project.name"/>
            </v-tabs>
            <v-window v-model="tab" v-for="project in projectData">
                <v-window-item :value="project.name">
                    <ProjectComponent 
                    :projectTitle="project.projectTitle" 
                    :projectOverview="project.projectOverview"
                    :githubLink="project.githubLink"
                    :websiteLink="project.websiteLink"
                    :websiteLinkDescription="project.websiteLinkDescription"
                    :projectImagePreviewSrc="project.projectImagePreviewSrc"
                    :toolIcons="project.toolIcons"
                    :toolImages="project.toolImages"
                    :leftDescriptionTitle="project.leftDescriptionTitle"
                    :leftDescriptionInfo="project.leftDescriptionInfo"
                    :rightDescriptionTitle="project.rightDescriptionTitle"
                    :rightDescriptionInfo="project.rightDescriptionInfo"/>
                </v-window-item>
            </v-window>
        </v-row>
    </v-container>
</template>

<script>
  import ProjectComponent from './ProjectComponent.vue'
  import projectData from '../assets/projectinfo.json'

  export default {
    data: () => ({
      tab: '',
      projectData: projectData
    }),
    components: {
      ProjectComponent
    }
  }
</script>