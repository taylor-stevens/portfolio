<template>
    <v-container class="fill-height">
        <v-row>
            <div class="text-h4" style="margin-top: 3%; margin-bottom: 3%;">
                {{ this.projectTitle }}
            </div>
            <div style="margin-bottom: 3%;">
                {{ projectOverview }}
                The
                <a key="projectTitle" :href="githubLink" title="projectTitle"
                    class="d-inline-block mx-2 social-link" rel="noopener noreferrer" target="_blank">
                    <v-icon :icon="'fa-brands fa-github'" size="24" style="color: white;"/>
                </a>
                <a :href="githubLink" target="_blank">current repository</a>
                <span :v-if="websiteLink">
                    and the <a :href="websiteLink" target="_blank">{{ this.websiteLinkDescription }}</a> can be found at these respective links.
                </span>
            </div>
        </v-row>
        <v-row justify-self="center" justify="center" style="margin-bottom: 3%;">
            <v-col cols="12" sm="11">
                <v-img :src="
                    projectImagePreviewSrc == 'fosteredfood' ? fosteredfood : 
                    projectImagePreviewSrc == 'coveytown' ? coveytown :
                    projectImagePreviewSrc == 'mlrm' ? mlrm : mlrm " justify-self="center"/>
            </v-col>
            <v-col cols='12' sm="1">
                <v-icon v-for="icon in toolIcons" :icon="icon" size="50" color="white"/>
                <v-icon v-for="image in toolImages" size="50">
                    <v-img :src="
                        image == 'jest' ? jest :
                        image == 'typescript' ? typescript :
                        image == 'numpy' ? numpy :
                        image == 'pandas' ? pandas :
                        image == 'scikit' ? scikit : scikit
                        "/>
                </v-icon>
            </v-col>
        </v-row>
        <v-row style="white-space: pre-wrap;">
            <v-col cols="12" sm="6">
                <div class="text-h5">
                    {{ leftDescriptionTitle }}
                </div>
                {{ leftDescriptionInfo }}
            </v-col>
            <v-col cols="12" sm="6">
                <div class="text-h5">
                    {{ rightDescriptionTitle }}
                </div>
                {{ rightDescriptionInfo }}
            </v-col>
        </v-row>
    </v-container>
</template>

<script>
// project images
import coveytown from '../assets/coveytown.png'
import fosteredfood from '../assets/fosteredfood.jpg'
import mlrm from '../assets/mlrm_overview.jpg'
// tool icons
import jest from '../assets/jest.png'
import typescript from '../assets/language-typescript.png'
import numpy from '../assets/numpy.png'
import pandas from '../assets/pandas.png'
import scikit from '../assets/scikit-learn.png'

export default {
    data: () => ({
        // images to render during build
        coveytown: coveytown,
        fosteredfood: fosteredfood,
        jest: jest,
        typescript: typescript,
        mlrm: mlrm,
        numpy: numpy,
        pandas: pandas,
        scikit: scikit
    }),
    props: {
        name: {
            type: String,
            default: 'Project Name'
        },
        projectTitle: {
            type: String,
            default: 'Project Loading', 
        },
        projectOverview: {
            type: String,
            default: 'Here will be a brief overview of the loading project. The repository link will be below.',
        },
        githubLink: {
            type: String,
            default: ''
        },
        websiteLink: {
            type: String,
            default: ''
        },
        websiteLinkDescription: {
            type: String,
            default: ''
        },
        projectImagePreviewSrc: {
            type: String,
            default: ''
        },
        toolIcons: {
            type: Object,
            default: []
        },
        toolImages: {
            type: Object,
            default: []
        },
        leftDescriptionTitle: {
            type: String,
            default: 'Project Specifics 1'
        },
        leftDescriptionInfo: {
            type: String,
            default: 'This will be information about the first project specifics.'
        },
        rightDescriptionTitle: {
            type: String,
            default: 'Project Specifics 2'
        },
        rightDescriptionInfo: {
            type: String,
            default: 'This will be information about the second project specifics.'
        }
    }
}
</script>