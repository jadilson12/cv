<template>
    <v-container class="width-limit-500 text-left pa-0 pt-2" >
        <v-layout column>
            <v-flex>
                <h3 class="subhead">{{ header }}</h3>
            </v-flex>
            <v-flex text-align-left>
                <ul>{{ content.description }}</ul>
                <ul class="italic">{{ content.additional }}</ul>
            </v-flex>
        </v-layout>
    </v-container>
</template>

<script>
export default {
    name: "formacao-text",
    props: ["content"],
    computed: {
        header() {
            return `${this.content.name} | ${this.content.year}`;
        },
        logoLink() {
            // not used at this point
            return `../../assets/${this.content.logo}`;
        }
    }
};
</script>
