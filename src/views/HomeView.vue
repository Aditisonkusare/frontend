<template>
  <v-app id="home">
    <NavBar />
    <v-container fluid>
      <div class="head">
            <v-row>
              <v-col cols="5">
                <div style="position:relative">
                <h1 class="text-grey">Hello,</h1>
                <h1 class="text-black">I'm Aditi Vilas Sonkusare</h1>
                <span class="text-grey"><h2>Graduate Software Developer</h2></span><br />
                <v-btn tile dark class="text-black" variant="outlined">Contact me</v-btn>
                </div>
              </v-col>
              <v-col cols="2">
                <div style="position:absolute;z-index:9999;bottom:0;margin-left:auto;margin-right: auto;left:0;right:0;text-align: center;">
                  <v-icon>fas fa-angle-double-down</v-icon>
                </div>
              </v-col>
              <v-col cols="5">
                <div style="position:relative;z-index:9999;" class="mt-16">
                  <vimg src="i1.png" contain max-height="300"></vimg> 
                </div>
              </v-col>
            </v-row>

      </div>
      <v-col cols="12" class="mt-16" id="about">
        <div>
          <v-row align="center">
            <v-col cols="12" sm="6">
              <div class="egg">
                <v-img src="i2.png" max-height="300" ></v-img>
              </div>
            </v-col>
            <v-col cols="12" class="d-flex flex-column align-center justify-center text-center">
              <h1 style="width: 200px;">About Me</h1>
              <div style="width: 120px; text-align: left">
                <v-slider v-model="slider2" color="yellow" track-color="grey" label="Profile Strength" :max="100" :min="0" step="1" show-ticks>

                </v-slider>
              </div>
              <h4 class="mt-4">Profile Summary</h4>
              <p class="text-grey" style="max-width: 800px; text-align: justify;"> Graduate Software Engineer with more than 1½ years of experience in tech industry specializing in 
                Backend API Development and Front-End Testing. Experienced in software development with a test-driven approach, utilizing modern JavaScript, 
                TypeScript and Python frameworks. Strong ability to understand client requirements and deliver successful releases. Highly adept at managing 
                multiple projects across diverse domains, ensuring efficiency and quality. Committed to delivering high-quality solutions while continuously 
                improving processes.</p>
              <br />
              <p class="text-grey" style="max-width: 800px; text-align: justify;"> With a foundation of Master’s Degree from University Of Galway in Computer Science specializing in Data Analytics, 
                Artificial Intelligence, Big Data and Digital Economy. I have a proven track record of delivering solutions with value and passion in
                learning from and work with experts in the field. Highly skilled in deep learning libraries such as NumPy, Matplotlib, Keras, PyTorch, 
                TensorFlow, and others. Aspiring for professional leadership through cutting-edge knowledge and teamwork.
              </p>
              <v-btn tile dark color="#5f2c95" class="mt-4">
                DOWNLOAD RESUME
              </v-btn>
              </v-col>
            </v-row>
          </div>
      </v-col>
      <div class="text-center mt-4">
        <h2>What do I do ?</h2>
        <div style="width:120px; margin: 0 auto">
          <v-slider v-model="slider2" color="#5f2c95" label="track-color"></v-slider>
        </div>
      </div>
      <v-col cols="12" class="padd" id="skills">
        <div class="first" id="project">
          <v-row>
            <v-col cols="12">
              <div class="child">
                <section id="skills" class="section">
                  <h1>Skills</h1>
                  <transition name="fade">
                    <div v-if="showSkills" class="child">
                      <ul>
                        <li v-for="(skill, index) in skills" :key="index">
                          {{ skill }}
                        </li>
                      </ul>
                    </div>
                  </transition>
                  <v-btn @click="toggleSkills">{{ showSkills ? 'Hide' : 'Show' }} Skills</v-btn>
                </section>
                <section id="projects" class="section">
                  <h1>Projects</h1>
                  <p>My past work...</p></section>
              </div>
            </v-col>
          </v-row>
        </div>
      </v-col>
    </v-container>
  </v-app>
</template>

<script>
import { defineComponent } from 'vue';

// Component
import NavBar from '@/components/NavBar.vue';

export default defineComponent({
  name: 'HomeView',
//   setup() {
//     return { 
//       slider2:50,
// items:[
//   { 
//     img: "i3.png" 
//   },
//   { 
//     img: "i4.png"
//   },
//   {
//     img: "i5.png" 
//   }
// ]
//   };
// },
  components: {
    NavBar
} 
});
</script>
<style scoped>
.v-container{
  padding:16px 0;
}
.head{
  position:relative;
  text-align:center;
  padding:12px;
  margin-bottom: 6px;
  height:400px;
  width:100%;
  color:white;
}
.head:before{
  content: " ";
  position:absolute;
  top:0;
  left:0;
  height:100%;
  width:50% ;
  background:lavender ;
  transform:skew(0deg, 6deg);
}
.head:after{
  content: " ";
  position:absolute;
  top:0;
  right:0;
  height:100%;
  width:50% ;
  background:lavender ;
  transform:skew(0deg, -6deg);
}
.egg{
  display:block;
  margin-left: 100px;
  margin-top: 50px;
  width:356px;
  height:300px;
  background-color: #5f2c95;
  border-radius: 50% 50% 50% 50% / 60% 60% 40% 0%;
}
.first {
  width:100%;
  height:280px;
  text-align:center;
  padding:2rem 2rem;
}
.child {
  display: inline-block;
  padding:2rem 1rem;
  vertical-align:middle;
  text-align:center;
  margin-right:8px;
}
.imgHover {
  padding: 0 200px;
}
.pre {
  width:100%;
  height: 380px;
  text-align: center;
  padding: 0 200px;
  background-color: #f5f5f5;
}
.hire {
  width:100%;
  height:200px;
  padding:0 200px;
  background-color: #e9e9e9;
  margin-top:-24px;
}
</style>
