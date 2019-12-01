<template>
  <v-container  text-left>
    <v-layout column>
      <v-flex>
        <v-layout row>
          <h3 v-text="content.title"></h3>
        </v-layout>
      </v-flex>
      <v-layout row>
        <v-flex text-align-left>
          <ul class="italic">{{ content.institution }}</ul>
          <ul>{{ content.description }}</ul>
        </v-flex>
        <v-tooltip top class="subhead">
          <v-btn icon text :href="content.link" slot="activator" target="_blank">
            <i class="fab fa-github"></i>
          </v-btn>
          <span>View project repo</span>
        </v-tooltip>
      </v-layout>
      <v-flex row class="justify-center">
        <v-chip
          v-for="(item, index) in content.techUsed"
          :key="item.title"
          @click.native="show(item.content, index)"
          slot="activator"
          :input-value="item.show"
        >{{ item.title }}
        </v-chip>
      </v-flex>
      <v-flex pt-2>
        <transition name="fade">
          <ul class="italic" v-if="showItem" v-text="showItemContent"></ul>
        </transition>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
    export default {
        name: "project-text",
        props: ["content"],
        data() {
            return {
                showItem: false,
                showItemContent: null
            };
        },
        methods: {
            show(item, index) {
                this.clearSelect();
                if (this.showItem && this.showItemContent === item) {
                    this.showItem = false;
                    this.content.techUsed[index].show = false;
                } else {
                    this.showItem = true;
                    this.showItemContent = item;
                    this.content.techUsed[index].show = true;
                }
            },
            clearSelect() {
                for (const item of this.content.techUsed) {
                    item.show = false;
                }
            }
        }
    };
</script>
<style>


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
</style>
