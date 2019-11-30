<template>
  <v-app ref="app">
    <v-container  v-if="!enter"  class="title-container">
      <v-layout column>
        <name-bar key="name-center"></name-bar>
        <enter-bar @enter="enterCV()"></enter-bar>
      </v-layout>
    </v-container>
    <transition name="slide-fade">
      <v-container v-if="enter" pl-0 pr-0>
        <v-layout column>
          <v-toolbar flat class="transparent" fixed text-center  height="160px">
            <v-layout column>
              <name-bar v-if="enter"></name-bar>
              <title-bar key="title" @changePage="change"></title-bar>
            </v-layout>
          </v-toolbar>
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
  data() {
    return {
      no: "none",
      enter: false,
      pageButton: "formacao",
      scroll: true
    };
  },
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
          this.pageButton = "skills";
          break;
        case 2:
          this.pageButton = "experience";
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
  min-width: 200px;
}
.content,
.content__wrap {
  padding: 0;
}
main.content {
  padding: 0;
}
.toolbar__content {
  justify-content: center;
  background-color: #eeeeee;
}
.application .theme--light.chip,
.theme--light .chip {
  background-color: grey-lighten-3;
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
.title-container {
  padding: 0;
  padding-top: 20px;
  max-width: 650px;
  max-height: 174px;
}
.divider-container {
  max-width: 500px;
  padding: 0;
  padding-bottom: 3;
  padding-top: 3;
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
.width-limit-1000 {
  max-width: 1000px;
}
.transparent-background {
  background-color: none;
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
