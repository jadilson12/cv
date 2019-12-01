<template>
  <v-container grid class="page">
    <transition name="fade" mode="out-in">
      <formacao-page v-if="pressed==='formacao'"></formacao-page>
      <about-page v-if="pressed==='about'"></about-page>
      <skills-page v-if="pressed==='habilidades'"></skills-page>
    </transition>
  </v-container>
</template>

<script>
    import AboutPage from "./AboutPage";
    import FormacaoPage from "./FormacaoPage";
    import SkillsPage from "./SkillsPage";

    export default {
        name: "page-show",
        props: ["pressed"],
        components: {
            SkillsPage,
            AboutPage,
            FormacaoPage
        }
    };
</script>

<style>
  .page {
    padding: 0;
  }

  /* Transitions */
  .fade-enter-active {
    transition: opacity 0.5s;
  }

  .fade-leave-active {
    transition: opacity 0.1s;
  }

  .fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */
  {
    opacity: 0;
  }

  .fade-enter-to,
  .fade-leave {
    opacity: 1;
  }

  /*Stylised*/
  .v-chip.v-size--default {
    font-size: 13px
  }

  .theme--light.v-chip {
    color: rgba(0, 0, 0, 0.90);
  }
</style>
