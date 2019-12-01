<template>
  <v-container class="width-limit-800 text-left" pa-0 pt-2 pb-2>
    <v-layout column>
      <!-- Title -->
      <v-flex>
        <v-layout row>
          <h3 class="subhead" v-text="content.title "></h3>
        </v-layout>
      </v-flex>
      <!-- Info -->
      <v-layout row class="subhead">
        <v-flex text-align-left pr-1>
          <ul class="italic subhead">{{ content.institution }}</ul>
          <ul>{{ content.description }}</ul>
        </v-flex>
        <v-tooltip top class="subhead">
          <v-btn icon flat :href="content.link" slot="activator" target="_blank">
            <i class="fab fa-github"></i>
          </v-btn>
          <span>View project repo</span>
        </v-tooltip>
      </v-layout>
      <v-flex row >
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
          <ul class="italic" v-if="showItem">{{ showItemContent }}</ul>
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
