<template>
  <v-app ref="app">
    <v-container v-if="!enter" class="title-container pt-0 mt-0">
      <v-layout column class="name-container" >
        <name-bar key="name-center"></name-bar>
        <enter-bar @enter="enterCV()"></enter-bar>
      </v-layout>
    </v-container>
    <transition name="slide-fade">
      <v-container v-if="enter" pl-0 pr-0 pb-2>
        <v-layout column>
          <v-app-bar flat color="#eeeeee" class="toolbar text-center " fixed app height="120px">
            <v-layout column>
              <name-bar v-if="enter"></name-bar>
              <title-bar key="title" @changePage="change"></title-bar>
            </v-layout>
          </v-app-bar>
          <v-content>
            <page-show :pressed="pageButton"></page-show>
          </v-content>
        </v-layout>
      </v-container>
    </transition>
  </v-app>
</template>

<script>
    import NameBar from './components/bar/NameBar'
    import EnterBar from './components/bar/EnterBar'
    import TitleBar from './components/bar/TitleBar'
    import PageShow from "./pages/PageShow";

    export default {
        name: 'App',
        components: {
            NameBar,
            EnterBar,
            TitleBar,
            PageShow
        },
        data: () => ({
            no: "none",
            enter: false,
            pageButton: "about",
            scroll: true
        }),
        methods: {
            onScroll() {
                this.scroll = window.pageYOffset === 0;
            },

            enterCV() {
                this.enter = true;
            },
            change(prop) {
                switch (prop) {
                    case 0:
                        this.pageButton = "about";
                        break;
                    case 1:
                        this.pageButton = "habilidades";
                        break;
                    case 2:
                        this.pageButton = "experienca";
                        break;
                    case 3:
                        this.pageButton = "formacao";
                        break;
                    default:
                        this.pageButton = null;
                }
            }
        },
    };
</script>

<style>

  .toolbar{
    height: 100px;
  }
  .slide-fade-enter-active {
    transition: all 0.3s ease;
  }

  .slide-fade-leave-active {
    transition: all 0.2s ease;
  }

  .slide-fade-leave-to {
    opacity: 0;
  }

  .slide-fade-enter {
    transform: translateY(150px);
    opacity: 0;
  }

  /* App Restyling */
  #app {
    font-family: "Roboto", sans-serif;
    color: #2c3e50;
    background-color: #eeeeee;
  }

  .content,
  .content__wrap {
    padding: 0;
  }

  main.content {
    padding: 0;
    max-width: 800px;
  }

  .toolbar__content {
    justify-content: center;
    background-color: #eeeeee;
  }

  .application .theme--light.chip,
  .theme--light .chip {
    background-color: #eeeeee;
  }

  .chip.chip--outline {
    border-color: #aa9ea4;
    color: #1b1b1b;
  }

  .chip:hover,
  .chip.chip--outline:hover {
    background-color: #135e5ab6;
    border-color: #135e5ab6;
  }

  .chip--selected {
    background-color: #135e5ab6 !important;
  }

  .chip--selected.chip--outline {
    background-color: #135e5ab6 !important;
  }

  .divider-container {
    max-width: 500px;
    padding: 3px 0;
  }

  .width-limit-500 {
    max-width: 500px;
  }

  .width-limit-600 {
    max-width: 600px;
  }

  .width-limit-800 {
    max-width: 800px;
  }

  .transparent-background {
    background-color: initial;
  }

  h1 {
    font-weight: 200;
    font-size: 56px;
  }

  h3 {
    font-weight: 200;
  }

  h2 {
    font-weight: 200;
  }

  .v-application ul, .v-application ol {
    padding-left: 0 !important;
  }

  .title-container {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100%;
    margin: 0 auto;
    padding: 0 auto;
  }
  .head {
    font-size: 25px;
  }
  .subhead {
    font-size: 20px;
  }
  .italic {
    font-style: italic;
  }
</style>
