<template>
  <v-container class="about-page">
    <v-container class="pt-0 pb-0">
      <v-layout row>
        <v-flex text-center>
          <v-avatar size="200px">
            <img src="https://avatars2.githubusercontent.com/u/36805474" alt="">
          </v-avatar>
        </v-flex>
        <v-flex>
          <v-container pt-4>
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
          </v-container>
        </v-flex>
      </v-layout>
    </v-container>
  </v-container>
</template>

<script>
    import InfoText from "../../components/txt/InfoText";
    import {profile} from '../../api/data'

    export default {
        name: "basic-info-bar-row",
        components: {InfoText},
        data: () => ({
            basic: profile.basic,
            additional: profile.additional
        })
    };
</script>
