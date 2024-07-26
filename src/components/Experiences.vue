<template>
    <v-container>
        <v-row>
            <v-col cols="12" v-for="experience in experiences">
                <Experience :experience="experience"/>
                <Experience v-if="experience.previouslyHeldPosition" :experience="experience.previouslyHeldPosition"/>                    
            </v-col>
        </v-row>
    </v-container>
</template>

<script>
    import Experience from './Experience.vue';
    import experiences from './data/experiences.json'

    export default {
        data: () => ({
            experiences: experiences
        }),
        components: {
            Experience
        }
    }
</script>