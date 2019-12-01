<template>
  <v-container class="name-container pb-0 mb-0"  text-center >
    <h1 id="small" v-text="initials"></h1>
    <h1 id="full" v-text="name"></h1>
    <v-divider></v-divider>
  </v-container>
</template>

<script>
export default {
  name: "name-bar",
  data() {
    return {
      name: "Jadilson Brandão Guedes",
      initials: "jbg"
    };
  }
};
</script>

<style>

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

.name-container {
  padding: 0;
  margin: 0;
  max-width: 642px !important;
}
.divider{
  width: 60%;
  display: flex;
  justify-content: center;
}
</style>
