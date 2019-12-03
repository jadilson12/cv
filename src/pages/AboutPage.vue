<template>
  <v-container text-center class="about-page width-limit-800">
    <basic-info-bar-row id="row"></basic-info-bar-row>
    <basic-info-bar-col id="col"></basic-info-bar-col>
    <v-container class="divider-container" pa-0 pt-3 pb-3>
      <v-divider></v-divider>
    </v-container>
    <v-card flat v-for="item in bio.content" :key="item" class="transparent">
      <v-card-text class="no-space text-left" v-text="item"></v-card-text>
    </v-card>
  </v-container>
</template>

<script>
    import BasicInfoBarCol from "../components/bar/BasicInfoBarRow";
    import BasicInfoBarRow from "../components/bar/BasicInfoBarCol";
    import {profile} from '../api/data'

    export default {
        name: "about",
        data: () => {
            return {
                bio: profile.bio
            };
        },
        components: {
            BasicInfoBarRow,
            BasicInfoBarCol
        }
    };
</script>
<style>
  @media (min-width: 651px) {
    #row {
      display: block;
      max-width: 600px;
    }

    #col {
      display: none;
    }
  }

  @media (min-width: 0px) and (max-width: 650px) {
    #row {
      display: none;
    }

    #col {
      display: block;
    }
  }

  .about-page {
    padding-top: 0;
    padding-bottom: 0;
  }

  .no-space {
    padding-top: 0;
    padding-bottom: 16px;
  }
</style>
