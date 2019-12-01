<template>
  <v-container class="width-limit-600 text-left pt-2" >
    <v-layout column>
      <v-flex>
        <h3 class="subhead" v-text="title"></h3>
      </v-flex>
      <v-flex text-align-left>
        <li v-for="item in content" :key="item" v-text="item"></li>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
  export default {
      name: "skills-text",
      props: ["title", "content"]
  };
</script>
