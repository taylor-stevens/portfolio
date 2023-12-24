<template>
    <v-container class="fill-height">
        <v-row>
            <v-col>
                <div class="text-h4" style="margin-top: 5%; margin-bottom: 3%;">
                    The FosteredFood Application: Cohesion of Mutual Aid Networks with Support from Technological Integration
                </div>
                <div style="margin-bottom: 3%;">
                    FosteredFood is a community-driven web application project developed in collaboration with 
                local community fridges, with the primary goal of mitigating concerns related to food access 
                and food sovereignty. This initiative involved the development of both software and low-cost 
                temperature sensors, which were sought to be deployed to enhance volunteer coordination, ensure
                food safety in the fridges, and share critical information about fridge contents with the public. 
                The project introduced both the software and hardware alongside qualitative fieldwork to evaluate 
                the effectiveness, adoption, and expected impact of the web application on the involved communities.
                The current site can be found <v-icon icon="mdi-github"/> {{ " " }}<a href="https://taylor-stevens.github.io/fostered-food/" target="_blank">here</a>
                along with the <a href="https://github.com/taylor-stevens/fostered-food" target="_blank">current repository</a>.
            </div>
            </v-col>
        </v-row>
        <v-row justify-self="center" justify="center" style="margin-bottom: 3%;">
            <v-col>
                <v-img src="./fosteredfood.jpg"
                justify-self="center"
                >
                </v-img>
            </v-col>
            <v-col cols="1">
                <v-container class="grow d-flex flex-column flex-nowrap">
                    <v-row>
                        <v-img src="../assets/react.png"></v-img>
                    </v-row>
                    <v-row>
                        <v-img src="../assets/language-javascript.png"></v-img>
                    </v-row>
                    <v-row>
                        <v-img src="../assets/nodejs.png"></v-img>
                    </v-row>
                    <v-row>
                        <v-img src="../assets/language-typescript.png"></v-img>
                    </v-row>
                    <v-row>
                        <v-img src="../assets/airballoon.png"></v-img>
                    </v-row>
                    <v-row>
                        <v-img src="../assets/docker.png"></v-img>
                    </v-row>
                    <v-row>
                        <v-img src="../assets/google-spreadsheet.png"></v-img>
                    </v-row>
                    <v-row>
                        <v-img src="../assets/google-plus.png"></v-img>
                    </v-row>
                    <v-row>
                        <v-img src="../assets/bootstrap.png"></v-img>
                    </v-row>
                    <v-row>
                        <v-img src="../assets/magnify-expand.png"></v-img>
                    </v-row>
                </v-container>
            </v-col>
        </v-row>
        <v-row>
            <v-col>
                <div class="text-h5">
                    Software
                </div>
                <br>
                At the heart of the project, the software framework revolved around React and Node.js as the primary 
                Javascript library and environment for the application. React was chosen for its ability to create 
                reusable UI components and efficiently update the user interface based on real-time data changes 
                without necessitating a complete page refresh. Coupled with Node.js, this allowed for a consistent 
                Javascript and Typescript ecosystem throughout the codebase. For the backend deployment, the project
                employed fly.io in conjunction with Docker. This choice was informed by its rapid configurability, 
                simplified image building from Dockerfiles, and user-friendly command line prompts, culminating in a 
                hassle-free deployment process. Furthermore, Fly.io's free accessibility aligns with the primary goals 
                of our project.
                <br><br>
                The database for the application relies on Google Sheets and the accompanying Google APIs. This selection 
                is motivated by its visibility, transparency, and user-friendliness for non-technical audiences. Further, 
                the Google Suite is accessible through multiple means including public web browsers at local libraries 
                as well as numerous personal devices, extending the accessibility of the project significantly. Implementing 
                async functions in the APIs enhances the application's efficiency and responsiveness, reducing the risk of 
                blocking code. Lastly, the repository uses the dotenv package to make the configuration-related information 
                more secure and organized.
                <br><br>
                The components of the application are built using React's functional components, enhancing simplicity, 
                consistency, and reusability. React Hooks API, including useEffect for updating elements and managing information
                 via contexts, is instrumental in streamlining the user experience. Within the functional components, the React 
                 Hook’s API is used not only to help update elements (useEffect) and to update the map, but also to easily keep 
                 track of information via contexts (useContext).
                <br><br>
                Alongside React’s Components and Hooks, the project also implements React’s Context Providers to propagate data 
                to children components. Context Providers play a crucial role in propagating data to child components, simplifying 
                state management, cross-component communication, and enhancing reusability. This made it easier to maintain 
                simplicity in the code when the data was fetched from the backend. It was also important in managing the global 
                state and sharing the data and functionality across the application without passing props down through multiple 
                layers of components, also known as prop drilling. Overall, the Contexts simplified state management while maintaining 
                successful cross-component communication. Without prop drilling, the application further became more readable and the 
                components were easier to re-use. Lastly, the Context Providers simplified testing components with the ability to provide 
                mock contexts that eliminated test dependency concerns. 
                <br><br>
                Alongside React’s features, Bootstrap is heavily employed for its consistent design, responsive layout, 
                cross-browser compatibility, and accessibility features. It aids in rendering placeholder components and 
                user notifications. In addition to this, it aids in reducing the need for time and resources surrounding
                front-end development. One way that it was used was for its placeholder components which allow for alternative
                rendering in situations where async functions have either not yet returned or have failed, as well as for 
                user notifications. 
                <br><br>
                For the Map rendering in the application, there were many tile providers to choose from. For this project, 
                we choose the Transport Map via the OpenStreetMap Tile provider. ‘OpenStreetMap is a free, editable map of the
                globe that is built by volunteers largely from scratch and released with an open-content license’. This tile 
                provider works well with Leaflet, ‘a modern open-source JavaScript library for mobile-friendly interactive map[s]’, 
                which met the requirements of the project scope which included working well with NodeJS and React and allowing for 
                interactivity within the application. Requests to the Tile Provider are made with the TileLayer react-leaflet library. 
                The Leaflet library further allows for easy user interaction such as panning over and zooming in on the map tiles, 
                which are both vital in user experience.
                <br><br>
            </v-col>
            <v-col>
                <div class="text-h5">
                    Hardware
                </div>
                <br>
                One of the main hardware requirements included the translation and transmission of temperature data via 
                TMP36 Temperature Sensors from Analog Devices to a publicly available Google Sheets. These sensors were chosen 
                as the test sensors were able to be donated, and in large batches they are a very cheap part. Further, the sensors 
                provide a wide range of temperature readings that are highly accurate and can be used in both refrigerators and freezers. 
                <br><br>
                In the test sensors, the HiLetgo ESP32 LoRa WiFi Arduino Boards were used in conjunction with 3.7V Rechargeable
                Lithium Batteries. Multiple of these batteries can be attached in parallel to multiply the mAh availability, 
                and they are also easily removable for recharging, making it a good long term and cheap solution. The board was 
                specifically chosen to help keep costs low and the batteries were chosen such that they could be reused and so 
                that the boards did not have to have a connection to power outside of the fridge. Further, these boards come equipped
                with WiFi transmission if the LoRa transmission were to fail, which allows for backup since most of the community 
                fridges are housed by restaurants (or stores) with public WiFi. By keeping modifications to existing structures minimal, 
                the project would be feasible for multiple mutual aid groups in the community fridge network. 
                <br><br>
                The data collected by the temperature sensor would be collected by the board and transmitted via LoRa 
                which requires less power over time, extending the shelf life of the temperature sensor boards. The data that 
                is populating the Web Application is currently being held in Google Sheets as a database, which is where the 
                sensor’s data would be pushed onto in real time were the boards to be installed. The last piece of the hardware
                required for successful installation is the enclosure that will protect it from moisture, extreme temperatures, 
                and small physical damage from movement. After a few tests on our team, the enclosures could be easily 3D printed 
                via a Computer Aided Design software, maintaining low cost of the project. 
            </v-col>
        </v-row>
    </v-container>
</template>

<script>
//
</script>