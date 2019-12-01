<template>
  <v-container class="about-page">
    <v-layout>
      <v-flex>
        <v-avatar size="200px">
          <img src="https://avatars2.githubusercontent.com/u/36805474" alt="">
        </v-avatar>
      </v-flex>
      <v-container>
        <v-layout column>
          <v-flex>
            <info-text
              v-for="item in basic"
              :key="item.title"
              :title="item.title"
              :content="item.content"
            ></info-text>
          </v-flex>
          <v-flex>
            <info-text
              v-for="item in additional"
              :key="item.title"
              :title="item.title"
              :content="item.content"
            ></info-text>
          </v-flex>
        </v-layout>
      </v-container>
    </v-layout>
  </v-container>
</template>

<script>
    import InfoText from "../../components/txt/InfoText";
    import {profile} from '../../api/data'

    export default {
        name: "basic-info-bar-col",
        components: {InfoText},
        data: () => ({
            basic: profile.basic,
            additional: profile.additional
        })
    };
</script>
