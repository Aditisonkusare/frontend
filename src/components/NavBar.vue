<template>
    <v-app-bar app color="#4B0082" dark flat class="px-12">
        <v-btn>
            <span class="avs-initials">AVS</span></v-btn>
        <v-spacer></v-spacer>
        <v-btn text @click="scroll('home')" >Home</v-btn>
        <v-btn text @click="scroll('about')" >About</v-btn>
        <v-btn text @click="scroll('skills')" >Skills</v-btn>
        <v-btn text @click="scroll('experience')" >Work experience</v-btn>
        <v-btn text @click="scroll('projects')" >Projects</v-btn>
        <v-btn text @click="scroll('biog')" >Education</v-btn>
        <v-btn text @click="scroll('contact')" >Contact</v-btn>
    </v-app-bar>
</template>

<script>
export default {
    methods: {
        scroll(refName) {
            const element =document.getElementById(refName);
            element.scrollIntoView({behavior: "smooth"});
        }
    }

}
</script>

<style>
.avs-initials {
  background: white;
  color: #4B0082;
  font-weight: bold;
  border-radius: 50%;
  width: 36px;
  height: 36px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 16px;
  margin-right: 8px;
}
</style>