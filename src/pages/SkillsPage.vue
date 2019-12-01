<template>
  <v-container text-center class="skills-page">
    <v-container class="width-limit-800">
      <v-layout row>
        <v-flex>
          <v-chip
            outlined
            :input-value="item.pressed"
            :key="index"
            v-for="(item, index) in skills"
            @click.native="selectSkills(index)"
            v-text="item.title"
          >{{ item }}
          </v-chip>
        </v-flex>
      </v-layout>
    </v-container>
    <v-container class="width-limit-800">
      <v-layout row>
        <v-flex>
          <transition-group name="fade-chip">
            <v-chip
              close
              color="grey"
              text-color="white"
              :key="item.title"
              v-for="item in skillsSelected"
              @click:close="selectSkills(skills.indexOf(item))"
            >{{ item.title }}
            </v-chip>
          </transition-group>
        </v-flex>
      </v-layout>
    </v-container>
    <transition-group name="reorder">
      <skills-text
        v-for="item in skillsExplained"
        :key="item.title"
        :title="item.title"
        :content="item.content"
      ></skills-text>
    </transition-group>
  </v-container>
</template>

<script>
    import SkillsText from "../components/txt/SkillsText";
    import {skillsInitial, skills} from '../api/data'

    export default {
        name: "skills",
        components: {SkillsText},
        data: () => ({
            skillsInitial: skillsInitial,
            skills: skills,
            skillsExplained: [],
            skillsSelected: []
        }),
        mounted() {
            this.skillsExplained = [...this.skillsInitial];
        },
        methods: {
            selectSkills(pressed) {
                if (this.skills[pressed].pressed) {
                    this.skills[pressed].pressed = false;
                    this.skillsSelected.splice(this.skillsSelected.indexOf(this.skills[pressed]), 1);
                    this.reorderSkills();
                    this.skills.splice(this.skills.length, 0, this.skills[pressed]);
                    this.skills.splice(pressed, 1);
                } else {
                    this.skills[pressed].pressed = true;
                    this.skillsSelected.splice(0, 0, this.skills[pressed]);
                    this.reorderSkills();
                }
            },
            reorderSkills() {
                this.skillsExplained = [...this.skillsInitial];
                for (
                    let itemIndex = this.skillsSelected.length - 1;
                    itemIndex > -1;
                    itemIndex--
                ) {
                    const item = this.skillsSelected[itemIndex];
                    for (const skill of this.skillsExplained) {
                        if (skill.tags.indexOf(item.title) !== -1) {
                            this.skillsExplained.splice(this.skillsExplained.indexOf(skill), 1);
                            this.skillsExplained.splice(0, 0, skill);
                        }
                    }
                }
            }
        }
    };
</script>
<style>
  .skills-page {
    padding-top: 0;
    padding-bottom: 0;
  }

  .reorder-move {
    transition: transform 1s;
  }

  .fade-chip-item {
    transition: all 1s;
    display: inline-block;
    margin-right: 10px;
  }

  .fade-chip-enter,
  .fade-chip-leave-to {
    opacity: 0;
    transform: translateY(30px);
  }

  .fade-chip-leave-active {
    position: absolute;
  }
</style>
