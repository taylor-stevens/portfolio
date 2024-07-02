<template>
    <v-container>
        <v-row>
            <v-col cols="12" md="6" v-for="experience in experiences">
                <v-card>
                    <v-card-item v-slot:prepend>
                        <div class="text-overline mb-1">
                            {{ experience.jobStartDate + ' - ' + experience.jobEndDate }}
                        </div>
                        <div class="text-h6">
                            {{ experience.jobTitle }}
                        </div>
                        <v-card-subtitle>{{ experience.jobCompany + ' in ' + experience.jobLocation }}</v-card-subtitle>
                    </v-card-item>
                    <v-card-text v-for="description in experience.jobDescription" style="padding-top: 0; padding-bottom: 2%;">
                        {{ description }}
                    </v-card-text>
                </v-card>
            </v-col>
        </v-row>
    </v-container>
</template>

<script>
    import experiences from './data/experiences.json'

    export default {
    data: () => ({
        experiences: experiences
    }),
    }
</script>