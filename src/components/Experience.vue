<template>
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
        <v-card :v-if="experience.previouslyHeldPosition">
            
        </v-card>
    </v-card>
</template>

<script>
    export default {
    data: () => ({
    }),
    props: {
        experience: {
            type: Object,
            default: {
                "jobTitle": "Job Title",
                "jobLocation": "Location, Place, Country",
                "jobCompany": "Job Company",
                "jobStartDate": "Month 01, Year",
                "jobEndDate": "Month 30, Year",
                "remote": false,
                "inPerson": true,
                "jobDescription": [
                    "A brief discription of this job"
                ],
            }
        },
    }
}
</script>