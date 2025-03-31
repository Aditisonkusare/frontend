<template>
    <v-app-bar app color="#4B0082" dark flat class="px-12">
        <v-btn>
            <v-icon color="white" left class="mr-2"> fas fa-signature</v-icon>ADITI SONKUSARE
        </v-btn>
        <v-spacer></v-spacer>
        <v-btn text @click="scroll('home')" class="text-yellow">Home</v-btn>
        <v-btn text @click="scroll('about')" >About</v-btn>
        <v-btn text @click="scroll('portfolio')" >Skills</v-btn>
        <v-btn text @click="scroll('services')" >Work experience</v-btn>
        <v-btn text @click="scroll('page')" >Projects</v-btn>
        <v-btn text @click="scroll('biog')" >Education</v-btn>
        <v-btn text @click="scroll('contact')" >Contact</v-btn>
    </v-app-bar>
</template>

<script>
export default {
    methods: {
        scroll(refName) {
            const element =document.getElementById(refName);
            element.scrollIntoView({behaviour: "smooth"});
        }
    }

}
</script>

<style>

</style>