<template>
  <v-app id="home">
    <NavBar />
    <v-container fluid>
      <div class="head">
            <v-row>
              <v-col cols="5" id="home">
                <div style="position:relative">
                <h1 class="text-grey">Hello</h1>
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
                <div style="position:relative;z-index:9999; margin-left: 180px;" class="mt-15">
                  <v-img src="aditiProfile.png" contain max-height="400" max-width="400" ></v-img> 
                </div>
              </v-col>
            </v-row>
      </div>
      <v-col cols="12" class="mt-6" id="about">
        <div>
          <v-row align="center">
            <v-col cols="12" sm="6">
              <!-- <div class="egg">
                <v-img src="i2.png" max-height="300" ></v-img>
              </div> -->
            </v-col>
            <v-col cols="12" class="d-flex flex-column align-center justify-center text-center">
              <h1 style="width: 200px;">ABOUT ME</h1>
              <div style="width: 120px; text-align: left">
                <!-- <v-slider v-model="slider2" color="yellow" track-color="grey" label="Profile Strength" :max="100" :min="0" step="1" show-ticks>                </v-slider> -->
              </div>
              <h4 class="mt-4">PROFILE </h4>
              <p class="black" style="max-width: 800px; text-align: justify;"> Graduate Software Engineer with more than 1½ years of experience in tech industry specializing in 
                Backend API Development and Front-End Testing. Experienced in software development with a test-driven approach, utilizing modern JavaScript, 
                TypeScript and Python frameworks. Strong ability to understand client requirements and deliver successful releases. Highly adept at managing 
                multiple projects across diverse domains, ensuring efficiency and quality. Committed to delivering high-quality solutions while continuously 
                improving processes.</p>
              <br />
              <p class="black" style="max-width: 800px; text-align: justify;"> With a foundation of Master’s Degree from University Of Galway in Computer Science specializing in Data Analytics, 
                Artificial Intelligence, Big Data and Digital Economy. I have a proven track record of delivering solutions with value and passion in
                learning from and work with experts in the field. Highly skilled in deep learning libraries such as NumPy, Matplotlib, Keras, PyTorch, 
                TensorFlow, and others. Aspiring for professional leadership through cutting-edge knowledge and teamwork.
              </p>
              <v-btn tile dark color="#5f2c95" class="mt-4" href="/resume.pdf" download>
                DOWNLOAD RESUME
              </v-btn>
              </v-col>
            </v-row>
          </div>
      </v-col>
      <v-col cols="12" id="skills">
        <div class="first" id="project">
          <v-row>
            <v-col cols="12">
              <div class="child">
                <section id="skills" class="section">
                  <h1>SKILLS</h1>
                  <button @click="showSkills = !showSkills" class="toggle-btn"> {{ showSkills ? 'Hide' : 'Show' }} Skills
                    <span class="arrow">{{ showSkills ? '▲' : '▼' }}</span>
                  </button>
                  <transition name="impactful-fade">
                    <div v-if="showSkills" class="skills-grid">
                      <div v-for="(items, category) in skills" :key="category" class="skill-card">
                        <h3>{{ category }}</h3>
                        <ul>
                          <li v-for="(item, idx) in items" :key="idx">{{ item }}</li>
                        </ul>
                      </div>
                    </div>
                  </transition>
                </section>
                <section id="experience" class="section">
                  <h1 class="text-center mb-6">EXPERIENCE</h1>
                  <v-container>
                    <v-row
                    v-for="(row, rowIndex) in chunkedExperiences"
                    :key="rowIndex"
                    justify="center"
                    class="mb-4"
                    >
                    <v-col
                    v-for="(experience, index) in row"
                    :key="index"
                    cols="12"
                    sm="6"
                    md="5"
                    >
                    <v-card elevation="0" class="pa-4 d-flex flex-column align-center h-100">
                      <v-avatar size="64">
                        <v-img
                        :src="experience.logo"
                        alt="Company logo"
                        cover
                        class="rounded-circle">
                      </v-img>
                    </v-avatar>
                      <h3 class="mt-4 font-weight-bold">{{ experience.title }}, {{ experience.company }}</h3>
                      <p class="text-subtitle-2 mb-2 grey--text">
                        {{ experience.location }} | {{ experience.date }}
                      </p>
                      <ul class="text-left" style="line-height: 1.6;">
                        <li v-for="(detail, i) in experience.details" :key="i">{{ detail }}</li>
                      </ul>
                    </v-card>
                  </v-col>
                </v-row>
              </v-container>
                </section>
                <section id="projects" class="Projects">
                  <h1 class="text-center mb-6">PROJECTS</h1>
                  <v-container>
                    <v-row v-for="(projectChunk, index) in chunkedProjects" :key="index">
                      <v-col cols="12" md="6" v-for="project in projectChunk" :key="project.title">
                        <v-card class="pa-4 mb-4">
                          <h3>{{ project.title }}</h3>
                          <p class="text-grey">{{ project.location }}</p>
                          <p class="text-grey">{{ project.date }}</p>
                          <ul>
                            <li v-for="(point, i) in project.details" :key="i">{{ point }}</li>
                          </ul>
                        </v-card>
                      </v-col>
                    </v-row>
                  </v-container>
                </section>
              </div>
            </v-col>
          </v-row>
        </div>
      </v-col>
    </v-container>
  </v-app>
</template>

<script>
import { defineComponent, ref, computed } from 'vue';

// Component
import NavBar from '@/components/NavBar.vue';

export default defineComponent({
  name: 'HomeView',
  components: {
    NavBar
},
setup() {
    const showSkills = ref(false);

    const skills = {
      'Programming Languages': ['Python', 'JavaScript', 'Typescript'],
      'Tools/Technologies': ['Tableau', 'Postman'],
      'Frontend Frameworks': [ 'VUE.JS', 'Cypress', 'CSS', 'HTML'],
      'DevOps & Cloud': ['Git', 'Git Actions', 'AWS Web Services'],
      'Data Analytics': ['PyTorch', 'TensorFlow', 'Keras']
    };

    const experiences = ref([
      {
        title: 'Graduate Software Engineer',
        company: 'Adaptemy',
        location: 'Dublin, Ireland',
        date: 'Nov 2024 – Present',
        logo: '/logos/adaptemyLogo.png',
        details: [
          'Developed and optimized backend API endpoints using Node.js, ExpressJS, and Cypress with a TDD approach.',
          'Conducted end-to-end testing using Cypress, improving performance and collaboration.',
          'Managed API responses and aligned them with evolving client requirements.',
          'Experience working in an Agile software development environment, processes and methodologies.',
          'Actively participated in Agile ceremonies including sprint planning, refinement, and retrospectives, while conducting code reviews to ensure best practices, high-quality code, and adherence to Agile methodologies.'
        ]
      },
      {
        title: 'Junior Data Analyst',
        company: 'Orcawise',
        location: 'Dublin, Ireland',
        date: 'Dec 2023 – May 2024',
        logo: '/logos/orcawiseLogo.png',

        details: [
          'Employed data cleaning and preprocessing methods to ready raw data for analysis, enhancing data quality which resulted in building machine learning models for relation extraction among named entities in a high-pace collaborative working environment.',
          'Leveraged statistical analysis and data visualization tools to discern key market trends and patterns, aiding data-driven decision-making.',
          'Regularly updated scraping scripts to adapt to changes in website structures, maintaining GDPR compliance.',
          'Documented the results and findings of the model fine-tuning tasks for future references.'
        ]
      },
      {
        title: 'Data Annotator Intern',
        company: 'University of Galway',
        location: 'Galway, Ireland',
        date: 'Jan 2023 – Aug 2023',
        logo: '/logos/uogLogo.png',
        details: [
          'Annotated documents improving processes to ensure 90% accuracy in document classification and annotation.',
          'Proficiently annotated 300+ documents in native languages into distinguishable sections including Ambiguous, Educationalists, Educational Institutions, Governing Bodies, Education Technology and other categories.',
          'Collaborated seamlessly with cross-functional teams, integrating data-driven insights into strategic planning, resulting in 15% improvement in response efficiently.'
        ]
      },
      {
        title: 'Project Analyst Intern',
        company: 'Artif-Intel Pvt. Ltd.',
        location: 'Mumbai, India',
        date: 'Oct 2021 – Feb 2022',
        logo: '/logos/artifintelLogo.png',

        details: [
          'Designed, implemented, and maintained ETL pipelines processes in Informatica PowerCenter to facilitate the migration of data from source to target systems after data quality assurance and cleansing.',
          'Utilized Git for version control in collaborative ML projects, reducing code conflicts by 15%.',
          'Conducted comprehensive assessments of underlying data structures, formats, quality issues, and dependencies.',
          'Ensured compliance with data security requirements stated by client as per GDPR norms maintaining a perfect track record of zero data breaches with the data migration team cohort.',
          'Participated in daily stand-up meetings to provide updates on progress, address any roadblocks, and coordinate with team members to ensure smooth project execution and adherence to agile methodologies.'
        ]
      }
    ]);

    const projects = ref([
      {
        title: 'Youtube Data Analysis',
        location: 'Dublin, Ireland',
        date: 'December 2024 – February 2025',
        details: [
          'Deployed an ETL process on the Airflow web server, storing ingested data in an AWS S3 bucket and transforming  it with AWS Glue before loading it into an AWS Athena database that served as the data lake.'
        ]
      },
      {
        title: 'Camera Radar Sensor Fusion for Accurate Radar Prediction',
        location: 'Dublin, Ireland',
        date: 'April 2023 – August 2024',
        details: [
          'Conducted cutting-edge research on sensor fusion methods, with a focus on the combination of radar and camera data within the framework of the lift splat shot model, leveraging transfer learning principles.'
        ]
      }
    ]);

    const chunkedExperiences = computed(() => {
      const chunks = [];
      for (let i = 0; i < experiences.value.length; i += 2) {
        chunks.push(experiences.value.slice(i, i + 2));
      }
      return chunks;
    });

    const chunkedProjects = computed(() => {
      const chunks = [];
      for (let i = 0; i < projects.value.length; i += 2) {
        chunks.push(projects.value.slice(i, i + 2));
      }
      return chunks;
    });
    return {
      showSkills,
      skills,
      experiences,
      projects,
      chunkedExperiences,
      chunkedProjects
    };
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
  display:inline-block;
  padding:2rem 1rem;
  vertical-align:middle;
  text-align:center;
  margin-right:8px;
}

.imgHover {
  padding:0 5%;
}

.pre {
  width:100%;
  height:380px;
  text-align:center;
  padding:0 5%;
  background-color:#f5f5f5;
}

.hire {
  width:100%;
  height:200px;
  padding:0 200px;
  background-color: #e9e9e9;
  margin-top:-24px;
}

.section {
  padding: 2rem;
  position: relative;
  z-index: 1;
}

.toggle-btn {
  margin-top: 1rem;
  padding: 0.6rem 1.2rem;
  background-color: #5f2c95;
  color: white;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  z-index: 2;
  position: relative;
}

.skills-grid {
  display: flex;
  justify-content: center;
  align-items: flex-start;
  gap: 2rem;
  flex-wrap: wrap; 
  overflow-x: visible;
  padding: 1rem 0;
}

.skill-card {
  min-width: 200px;
  background-color: #f9f9f9;
  border-radius: 16px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.08);
  padding: 1rem 1.5rem;
  text-align: center;
  flex-shrink: 0;
}

.skill-card:hover {
  transform: translateY(-4px);
}

.skill-card h3 {
  font-size: 1.1rem;
  margin-bottom: 0.8rem;
  font-weight: 600;
  color: #333;
  border-bottom: 2px solid #ccc;

}

.skill-card ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.skill-card li {
  margin: 6px 0;
  font-size: 0.95rem;
  color: #444;
}

/* Mobile responsiveness */
@media screen and (max-width: 768px) {
  .egg {
    width: 80%;
    height: auto;
    margin-top: 2rem;
  }

  .child {
    display: block;
    width: 100%;
    margin-right: 0;
    padding: 1rem 0;
  }

  .first {
    padding: 1rem;
    height: auto;
  }

  .pre,
  .hire,
  .imgHover {
    padding: 0 1rem;
  }

  .skill-card {
    min-width: 100%;
  }

  .head {
    padding: 1rem;
    min-height: 260px;
  }

  .toggle-btn {
    width: 100%;
  }
}

</style>

