<template>
  <v-container  text-left class="pl-0">
    <v-layout column>
      <v-flex>
        <v-layout row>
          <h3 class="pl-3" v-text="header"></h3>
        </v-layout>
      </v-flex>
      <v-flex text-align-left>
        <ul class="pl-0" v-text="content.description"></ul>
      </v-flex>
      <v-flex row class="justify-center" >
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
          <ul class="italic"  v-if="showItem" v-text="showItemContent"></ul>
        </transition>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
    export default {
        name: "experience-text",
        props: ["content"],
        computed: {
            header() {
                return `${this.content.title} \n| ${this.content.company} | ${
                    this.content.date
                }`;
            }
        },
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
