<template>
  <v-container pa-0 class="text-center">
    <v-btn @click.native="enter" icon>
      <i class="fas fa-arrow-down"></i>
    </v-btn>
  </v-container>
</template>

<script>
export default {
  name: "enter-bar",
  methods: {
    enter() {
      this.$emit("enter");
    }
  }
};
</script>
<style>
</style>
