<template>
  <v-container class="name-container text-center">
    <h1 id="small" v-text="abv"></h1>
    <h1 id="full" v-text="name"></h1>
    <v-divider></v-divider>
  </v-container>
</template>

<script>
    import {profile} from '../../api/data'

    export default {
        name: "name-bar",
        data: () => ({
            name: profile.name,
            abv: profile.abv
        })
    };
</script>
<style>

  .name-container {
    margin: 0 auto !important;
    padding: 0 !important;
    max-width: 642px !important;
  }

  @media (min-width: 697px) {
    #small {
      display: none;
    }

    #full {
      display: block;
    }
  }

  @media (min-width: 0px) and (max-width: 696px) {
    #full {
      display: none;
    }

    #small {
      display: block;
    }
  }

</style>
