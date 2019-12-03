<template>
  <v-container class="text-center">
    <v-footer fixed app>
      <v-btn
        icon
        small
        :href="bio.github"
        target="_blank"
        class="mr-8 text-capitalize"> GitHub <i class="fab fa-github-square ml-1"></i>
      </v-btn>
      <div class="mb-0 text-capitalize"> Made with
        <i class="fas fa-heart fa-sm"></i>
        Vue
        <v-btn
          icon
          small
          :href="bio.linkedin"
          target="_blank"
          class="ml-8 text-capitalize "> LinkedIn <i
          class="fab fa-linkedin ml-1"></i>
        </v-btn>
      </div>
    </v-footer>
  </v-container>
</template>

<script>
    import {profile} from '../../api/data'

    export default {
        name: "FooterBar",
        data: () => ({
            bio: profile.bio
        })
    }
</script>
<style>

  .v-btn__content {
    font-size: 12px;
  }
  .v-footer {
    font-size: 10pt;
    justify-content: center;
    padding: 5px 16px !important;
  }

  .theme--light.v-footer {
    border-top: 1px solid #ddd;
    background-color: #eeeeee;
    color: rgba(0, 0, 0, 0.87);
  }
</style>

