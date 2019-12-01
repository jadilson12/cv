<template>
  <v-container flat class="experience-page width-limit-800" text-left>
    <h3 class="head">Experiência de trabalho</h3>
    <experience-text v-for="item in experiences" :key="item.company" :content="item"></experience-text>
    <v-container class="divider-container" pa-0 pt-3 pb-3>
      <v-divider></v-divider>
    </v-container>
    <h3 class="head">Projetos</h3>
    <project-text v-for="item in projects" :key="item.company" :content="item"></project-text>
  </v-container>
</template>

<script>
    import ExperienceText from "../components/txt/ExperienceText.vue";
    import ProjectText from "../components/txt/ProjectText";
    import {experiences, projects} from '../api/data'
    export default {
        name: "experience",
        data() {
            return {
                projects: projects,
                experiences: experiences,
            };
        },
        components: {
            ExperienceText,
            ProjectText
        }
    };
</script>
<style>
  .experience-page {
    padding-top: 0;
    padding-bottom: 0;
  }
</style>P
