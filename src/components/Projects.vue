<template>
    <v-container justify="center" justify-self="center">
        <v-row no-gutters justify="center">
            <v-col>
                <v-tabs v-model="tab" fixed-tabs color="deep-purple-accent-4">
                    <v-tab :value="1">FosteredFood</v-tab>
                    <v-tab :value="2">Addressing Political Bias</v-tab>
                    <v-tab :value="3">Covey-Town</v-tab>
                </v-tabs>
                <v-window v-model="tab">
                    <v-window-item
                        :value="1"
                    >
                        <FosteredFood/>
                    </v-window-item>
                    <v-window-item
                        :value="2"
                    >
                        <PoliticalBias/>
                    </v-window-item>
                    <v-window-item
                        :value="3"
                    >
                        <Covey/>
                    </v-window-item>
                </v-window>
            </v-col>
        </v-row>
    </v-container>
</template>

<script>
  import FosteredFood from './FosteredFood.vue'
  import PoliticalBias from './PoliticalBias.vue'
  import Covey from './Covey.vue'

  export default {
    data: () => ({
      tab: null,
    }),
    components: {
      FosteredFood,
      PoliticalBias,
      Covey
    }
  }
</script>